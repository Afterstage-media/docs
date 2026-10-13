# Publicación de medios locales con Cloudflare Tunnel

El gestor puede publicar fotos, carruseles, videos y Reels cuyos archivos permanecen en la PC o servidor local. Meta no recibe normalmente el archivo directamente: recibe una URL HTTPS pública y descarga el recurso durante la creación del media container.

```text
archivo local → /media del gestor → Cloudflare Tunnel → URL HTTPS → Meta → Instagram
```

## Configuración

En `social-manager/.env`:

```env
MEDIA_ROOT=/app/media
# Para un túnel nombrado estable:
CLOUDFLARE_TUNNEL_URL=https://media.example.com
# Alternativas: PUBLIC_MEDIA_BASE_URL o PUBLIC_BASE_URL
```

El backend solo expone `MEDIA_ROOT` bajo `/media`, desactiva el listado de directorios y valida que cada ruta quede dentro de esa raíz. No se expone la computadora completa. Los nombres generados por la subida son aleatorios.

El `docker-compose.yml` incluye dos perfiles:

- `quick-tunnel`: URL temporal `trycloudflare.com`, útil para validar Meta.
- `named-tunnel`: URL estable de producción usando un token de Cloudflare.

Prueba rápida con Docker:

```bash
docker compose --profile quick-tunnel up -d
docker compose logs -f cloudflared-quick
```

Copiar la URL `https://…trycloudflare.com` que aparece en los logs y ponerla en `CLOUDFLARE_TUNNEL_URL` y `PUBLIC_BASE_URL` de `social-manager/.env`. Reiniciar `social-manager` después de guardar la URL.

La alternativa manual, desde la máquina que puede alcanzar el servidor local, es:

```bash
cloudflared tunnel --url http://localhost:8787
```

Copiar la URL `https://…trycloudflare.com` en `CLOUDFLARE_TUNNEL_URL` y reiniciar el gestor. Para una operación permanente conviene un túnel nombrado con subdominio propio y actualizar esa variable de manera estable. No usar Cloudflare Access en la ruta que Meta debe descargar.

Para producción, crear el túnel en Cloudflare, asignar el hostname al servicio web y levantarlo así:

```bash
export CLOUDFLARE_TUNNEL_TOKEN='token-del-tunel'
docker compose --profile named-tunnel up -d
```

El túnel apunta al servicio `website:80`, que publica el medio completo. No apuntar directamente a `social-manager:8787`: de ese modo se saltea el sitio público y el proxy de rutas. Configurar el hostname final también en `PUBLIC_BASE_URL` y `CLOUDFLARE_TUNNEL_URL`.

## Scheduler y estados

La aplicación guarda la programación en MongoDB y crea el container recién cuando llega `scheduledAt`. No crea containers con días de anticipación porque pueden vencer. El scheduler consulta cada 30 segundos y reclama el registro mediante una actualización atómica antes de publicar.

Estados de la aplicación:

```text
scheduled → publishing → published
                     ↘ scheduled (reintento)
                     ↘ failed (sin reintentos restantes)
```

Cada intento guarda `attempts`, `nextAttemptAt`, `containerId`, `publishedMediaId` y `lastError`. Si Meta ya entregó un `containerId`, el siguiente intento consulta ese container antes de crear otro para reducir duplicados.

Backoff inicial: 30 segundos, 2 minutos, 5 minutos y 15 minutos. Errores de token, permisos, formato, archivo inexistente o `Content-Type` incorrecto no se reintentan automáticamente.

## Requisitos de la URL

Antes de llamar a Meta, el backend comprueba `HEAD` sobre cada recurso. La respuesta debe ser pública, HTTPS, sin cookies ni autenticación, y devolver un tipo `image/*` o `video/*`. `localhost`, una IP privada y una URL protegida por Cloudflare Access no sirven para Meta.

## Instagram

- Una imagen usa `image_url`.
- Varias imágenes se convierten en carrusel.
- Un video usa `media_type=REELS` y `video_url`.
- Una historia usa `media_type=STORIES`.
- El backend espera `FINISHED` antes de llamar a `media_publish`.

El túnel y el servidor HTTP deben permanecer activos desde la creación del container hasta que Meta termine de descargar y procesar el archivo. Después de publicar, el recurso puede dejar de exponerse si no se necesita para otra finalidad.

## Seguridad

- El token de Meta solo vive en el backend.
- Se sirven únicamente archivos dentro de `MEDIA_ROOT`.
- Se bloquean rutas fuera de la raíz y listados de directorios.
- La API pública no permite crear containers.
- La simulación no llama a Meta ni necesita túnel.
- Para videos grandes, conservar el soporte HTTP de rangos del servidor/proxy y configurar límites acordes al tamaño real.

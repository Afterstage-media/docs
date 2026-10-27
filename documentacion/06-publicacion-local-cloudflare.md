# Medios, Cloudflare y almacenamiento R2

## Decisión de arquitectura

En producción, Afterstage no debe depender de la miniPC ni del filesystem local para servir fotos o videos públicos. El camino esperado es una subida directa al bucket R2 mediante el gateway de medios:

```text
frontend → backend/gateway → URL firmada → Cloudflare R2 → CDN/URL pública → nota o cobertura
```

El almacenamiento local y el túnel para medios quedan limitados a desarrollo, diagnóstico o compatibilidad explícita. No confundir el túnel del sitio con el almacenamiento de assets.

## Contrato productivo

Configurar en el backend:

```env
MEDIA_GATEWAY_URL=https://media-gateway.example.com
MEDIA_PUBLIC_BASE_URL=https://media.afterstage.ar
MEDIA_GATEWAY_SERVICE_TOKEN=secreto-del-gestor-de-secretos
```

El frontend se construye con `VITE_R2_MEDIA_UPLOADS=true` solo cuando el gateway, bucket, dominio y límites están probados. La variable no debe habilitarse como promesa si la infraestructura todavía no está operativa.

El gateway debe:

- autenticar la reserva servidor-a-servidor;
- validar tamaño, MIME y cuota antes de emitir la URL;
- usar claves aleatorias y expiración corta;
- impedir path traversal, SSRF y destinos privados;
- devolver únicamente metadatos y URLs públicas permitidas;
- registrar auditoría sin guardar secretos ni archivos innecesarios.

## Desarrollo local

Para pruebas aisladas puede usarse `MEDIA_ROOT` y una URL de túnel. Ese flujo no es producción y no debe quedar como default del despliegue público:

```env
MEDIA_ROOT=/app/media
PUBLIC_MEDIA_BASE_URL=https://media-dev.example.com
```

Cloudflare Tunnel puede exponer el sitio web completo mediante el servicio `website:80`. No apuntar a una computadora personal como CDN permanente ni dejar una URL `trycloudflare.com` como configuración productiva.

## Validación antes de habilitar R2

1. Confirmar cuenta, plan, bucket, dominio y política de retención.
2. Probar reserva, subida, lectura pública y expiración de URL.
3. Probar MIME correcto/incorrecto, tamaño, cuota, reintento y cancelación.
4. Confirmar que el token solo exista en Secret de producción.
5. Subir una imagen de prueba no sensible y verificar crédito, URL y eliminación según política.
6. Revisar logs y readiness sin exponer rutas internas.

## Instagram y URLs públicas

Cuando Meta necesite descargar un recurso, la URL debe ser HTTPS, pública, sin cookies ni autenticación y devolver un `Content-Type` compatible. `localhost`, IPs privadas y Cloudflare Access no sirven para ese paso.

La publicación de Instagram queda separada de la subida: el backend puede simular el flujo sin llamar a Meta, y una publicación real requiere credenciales y permisos verificados.

## Estado conocido

La existencia del gateway no implica que R2 esté habilitado en producción. Consultar [`10 · Estado actual y brechas`](./10-estado-actual-y-brechas.md) antes de anunciar fotos remotas como capacidad disponible.

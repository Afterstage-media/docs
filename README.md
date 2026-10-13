# Medio Under

Medio/comunidad de cultura under: historias, agenda, oportunidades freelance, descuentos para producir y experiencias de fans. El repositorio contiene la POC pública original y un gestor editorial y de redes ejecutable por separado.

## Objetivo editorial

El objetivo no es solamente publicar en redes: es convertir a Medio Under en un medio reconocible y confiable para conseguir acreditaciones de prensa en eventos y recitales. Cada nota, cobertura, crédito y contacto debe construir un historial que podamos presentar a productoras, salas, sellos y agencias.

Por eso el gestor prioriza consistencia editorial, trazabilidad de fuentes, calidad visual, créditos completos y un archivo público de coberturas. La publicación automática es una herramienta para sostener esa presencia; la reputación periodística es el producto principal.

## Cómo verlo

La interfaz pública está construida con React y Vite en [`frontend`](./frontend). En desarrollo se ejecuta con `npm install && npm run dev`; en producción Vite genera el `dist` que sirve Nginx.

### GitHub Pages

El workflow [`pages.yml`](./.github/workflows/pages.yml) publica la SPA automáticamente al hacer push a `main` (o manualmente desde Actions). En la configuración del repositorio, seleccionar **Settings → Pages → Source: GitHub Actions**. El build detecta automáticamente la ruta de un repositorio de proyecto (`https://<usuario>.github.io/<repo>/`), conserva las rutas de React mediante un fallback `404.html` y usa Node 24.

GitHub Pages sólo sirve el frontend estático. Para que agenda, notas, formularios y administración tengan datos reales, configurar `VITE_API_BASE_URL` en el entorno de build apuntando a la URL HTTPS del backend (por ejemplo, el dominio del Cloudflare Tunnel). Esa variable sólo contiene una URL pública; los secretos permanecen en el backend.

## Gestor editorial y de redes

El módulo [`social-manager`](./social-manager) permite crear notas, elegir imágenes, preparar copys, mover contenido por estados editoriales, programar publicaciones y publicar en Instagram/Facebook. Incluye un servidor MCP para operar el mismo flujo desde un asistente de IA.

```bash
cp social-manager/.env.example social-manager/.env
# editar ADMIN_TOKEN y las integraciones necesarias
docker compose up --build
```

Abrí `http://localhost:8080` para el sitio y la redacción React en `/admin`; `http://localhost:8787` expone el backend directo. El proxy web conecta `/api`, `/media`, RSS, sitemap y el dossier con el backend. MongoDB Atlas es obligatorio mediante `MONGODB_URI`; el backend no inicia sin esa variable. La publicación usa la API oficial de Meta Graph: es más estable, auditable y compatible con Docker que automatizar una sesión de Chrome con Selenium. Las imágenes que Meta descargue deben estar expuestas en una URL HTTPS pública configurada mediante `PUBLIC_BASE_URL`.

Para una URL pública temporal: `docker compose --profile quick-tunnel up -d` y consultar `docker compose logs -f cloudflared-quick`. Para producción, exportar `CLOUDFLARE_TUNNEL_TOKEN` y usar `docker compose --profile named-tunnel up -d`. La guía completa está en [`documentacion/06-publicacion-local-cloudflare.md`](./documentacion/06-publicacion-local-cloudflare.md).

También hay manifests nativos para k3s en [`deploy/k3s`](./deploy/k3s). Incluyen Deployments, Services, PVC persistentes, probes y Cloudflare Tunnel rápido o nombrado.

Para que k3s siga automáticamente la última versión de GitHub, aplicar los recursos de Flux documentados en [`deploy/flux`](./deploy/flux). GitHub Actions publica las imágenes en GHCR y Flux las reconcilia en el cluster.

La configuración completa, los permisos de Meta, las herramientas MCP y las decisiones de seguridad están en [`social-manager/README.md`](./social-manager/README.md).

## Documentación

- [`documentacion/01-vision.md`](./documentacion/01-vision.md) — idea, público y propuesta de valor.
- [`documentacion/02-arquitectura.md`](./documentacion/02-arquitectura.md) — mapa de páginas y recorridos.
- [`documentacion/03-sistema-visual.md`](./documentacion/03-sistema-visual.md) — dirección de arte y componentes.
- [`documentacion/04-mvp.md`](./documentacion/04-mvp.md) — alcance del MVP y siguientes pasos.
- [`documentacion/06-publicacion-local-cloudflare.md`](./documentacion/06-publicacion-local-cloudflare.md) — medios locales, Cloudflare Tunnel y scheduler de Meta.
- [`documentacion/07-seguridad.md`](./documentacion/07-seguridad.md) — controles aplicados, configuración y riesgos residuales.
- La arquitectura interna está documentada en [`social-manager/README.md`](./social-manager/README.md), con separación por dominio, aplicación, infraestructura e interfaces.

## Sitio público y comunidad

- Inicio editorial conectado al feed publicado y tablero de oportunidades.
- Comunidad de noteros, fotógrafos, bandas y cronistas.
- Portfolio fotográfico y videográfico por perfil.
- Columnas de cronistas y periodistas.
- Perfil de banda con agenda propia.
- Agenda de shows con filtros.
- Directorio autenticado de bandas, artistas, managers, salas, festivales, sellos y contactos en `/directorio` y `/admin/directorio`.
- Comunidad y publicación de oportunidades o historias con autenticación y roles específicos.

## Prompt original

> La idea es un gestor de redes páginas.... Quiero gestionar un medio de música.. Esta el repo de medio under (ese si esta en git)... La idea es crear notas ahí y subirlas a Instagram... Elegir fotos, crear copys, notas completas etc... La idea es que tenga un mcp para gestionar con IA varias cosas... Crea una rama nueva del repo del medio agregando todo esto... Incluí un back para publicar en meta con seleniun o con algúno similar, el que sea mejor... Idealmente sería que use un docker para que sea más limpia la publicación...
>
> Crea un readme con el promt original y un checklist de tareas refinadas

## Checklist refinado

### Base funcional

- [x] Crear una rama de trabajo sin modificar `main`.
- [x] Mantener la POC pública existente sin acoplarla al gestor.
- [x] Incorporar un panel editorial responsive con búsqueda y filtros.
- [x] Crear y editar notas, posts, carruseles, reels e historias.
- [x] Gestionar título, bajada, cuerpo, etiquetas, canales y fecha programada.
- [x] Subir hasta diez imágenes o asociar URLs públicas.
- [x] Persistir datos y archivos en volúmenes Docker.
- [x] Usar MongoDB para producción, con índices para agenda, estados y seguimiento.
- [x] Exigir MongoDB como persistencia única del backend.
- [x] Guardar latitud/longitud en eventos y directorio, calcular distancia y filtrar por radio.
- [x] Mantener un directorio de bandas, integrantes, managers, salas, festivales y contactos con redes, teléfonos y emails.
- [x] Servir medios locales de forma segura mediante `/media`.
- [x] Integrar URL pública configurable para Cloudflare Tunnel.
- [x] Esperar el procesamiento de Meta, guardar container IDs y aplicar reintentos con backoff.
- [x] Crear un dossier de prensa público con misión, audiencia, equipo, coberturas y datos de contacto.
- [x] Mantener un archivo de coberturas con evento, artista, ciudad y fecha.

### Flujo y publicación

- [x] Modelar estados: idea, borrador, revisión, aprobado, programado, publicando, publicado y error.
- [x] Validar transiciones para impedir publicaciones accidentales.
- [x] Añadir una simulación de publicación sin efectos externos.
- [x] Publicar imágenes y carruseles de Instagram mediante Meta Graph API.
- [x] Publicar posts con o sin imagen en páginas de Facebook.
- [x] Ejecutar automáticamente el contenido programado.
- [x] Registrar IDs remotos y errores de publicación sin exponer tokens.
- [ ] Validar una publicación real contra la cuenta Meta de Medio Under.
- [x] Agregar soporte específico para video/Reels y Stories en Meta.
- [x] Registrar el evento y la cobertura asociada a cada publicación.
- [x] Generar un enlace de cobertura para adjuntar a solicitudes de prensa.

### IA y MCP

- [x] Integrar un proveedor de IA compatible con la API de OpenAI.
- [x] Generar notas completas, copys sociales y mejoras editoriales.
- [x] Detectar y bloquear notas duplicadas o muy similares, con endpoint de previsualización y explicación de coincidencias.
- [x] Indicar al modelo que no invente hechos, citas ni créditos.
- [x] Exponer por MCP: listar, obtener, crear, editar, generar y publicar.
- [x] Hacer que MCP simule por defecto las publicaciones.
- [x] Incorporar búsqueda de contexto y fuentes del sitio para enriquecer notas.
- [x] Añadir aprobación por roles antes de habilitar una publicación real desde MCP.
- [x] Añadir herramientas MCP para preparar dossiers, registrar coberturas y gestionar solicitudes de acreditación.

### Operación y seguridad

- [x] Proteger la API con un token administrativo y mantener MCP como transporte stdio local.
- [x] Ejecutar el contenedor como usuario sin privilegios.
- [x] Limitar tamaño, cantidad y tipos de archivos subidos.
- [x] Separar secretos en `.env`, excluido de Git.
- [x] Añadir healthcheck, pruebas unitarias y compilación TypeScript estricta.
- [x] Usar MongoDB como persistencia única de producción.
- [x] Añadir autenticación por roles, auditoría, rate limit y backups.
- [x] Usar roles múltiples y permisos granulares por usuario, con acceso separado para Instagram.
- [x] Añadir rol auditor de sólo lectura y aprobación automática inicial de propuestas, configurable para volver a revisión manual.
- [x] Conectar el sitio público al backend mediante proxy Docker.
- [x] Generar RSS, sitemap, robots, metadatos SEO, autoría, fuentes y créditos fotográficos.
- [x] Recibir propuestas públicas como ideas editoriales moderables.
- [x] Registrar vistas y métricas editoriales básicas.
- [ ] Desplegar detrás de HTTPS y configurar almacenamiento de medios público (S3/R2 o equivalente).

### Prensa y crecimiento

- [x] Modelar productoras, salas, sellos, agencias y contactos de prensa.
- [x] Gestionar solicitudes: evento, fecha, responsable, estado, fecha de seguimiento y resultado.
- [x] Preparar, simular y enviar solicitudes por SMTP configurable.
- [x] Enviar mails con identidad del medio, `reply-to` y plantillas HTML/texto.
- [x] Agregar usuarios por roles, rate limiting y auditoría de requests.
- [x] Integrar el archivo editorial publicado en la SPA React mediante el feed público.
- [x] Agregar health/readiness, estado del scheduler, logs JSON y backup operativo.
- [x] Crear y editar el dossier del medio desde el panel de prensa.
- [x] Medir coberturas publicadas, respuestas, acreditaciones obtenidas y recitales cubiertos en el snapshot operativo.
- [x] Definir una política de cobertura y un código de créditos para sostener la confianza.

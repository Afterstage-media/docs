# Seguridad operativa

## Controles aplicados

- Autorización por roles (`admin`, `editor`, `press`, `directory`, `community`) en cada grupo de rutas privadas.
- Los Bearer JWT se validan con HS256, expiración, issuer/audience y firma del backend; el `sub` se contrasta contra la colección `users` de MongoDB y el rol efectivo sale de la base, no del token.
- Tokens comparados con comparación de tiempo constante; no se aceptan cookies de sesión.
- Rate limit global y límite específico para propuestas públicas.
- Headers defensivos: CSP, `X-Content-Type-Options`, `X-Frame-Options`, Referrer Policy y HSTS bajo HTTPS.
- Auditoría JSONL con rotación de tamaño; no se registran query strings que puedan contener secretos.
- Las cargas solo aceptan tipos permitidos, tamaño limitado y firmas binarias compatibles con el MIME declarado.
- No se sirve `/uploads`; solo `/media` y únicamente para los archivos que el flujo editorial necesita exponer.
- Validación de URLs de medios contra localhost, rangos privados, link-local y dominios internos para evitar SSRF.
- Escape de HTML/XML en artículos, dossier y RSS.
- El feed público usa un DTO explícito y no expone tokens, IDs remotos, intentos, errores ni datos operativos internos.
- El proxy Nginx aplica CSP y Permissions-Policy también a los assets estáticos de la SPA.
- Contenedores sin privilegios en el gestor y túneles; PVC separados para datos y medios.
- Los puertos Docker se enlazan a localhost; la exposición externa debe ser Cloudflare Tunnel.

## Configuración obligatoria

En producción definir `NODE_ENV=production`, `JWT_SECRET`, `MONGODB_URI`, `PUBLIC_BASE_URL` y `CLOUDFLARE_TUNNEL_URL`. Usar `TRUST_PROXY=true` únicamente cuando el proceso reciba tráfico exclusivamente desde el Nginx/Ingress controlado. La autenticación usa exclusivamente JWT emitidos por `/api/auth/login`; no se aceptan tokens opacos ni `X-API-Key`.

La colección `users` contiene documentos `{ _id, role, active }`. Se puede provisionar o revocar un usuario con `npm run users:upsert -- <id> <admin|editor|press> [true|false]`; el JWT debe llevar ese `id` en `sub` y una expiración (`exp`).

No publicar `secret.example.yaml` con valores reales. Crear el Secret desde un gestor de secretos o aplicar un archivo fuera del repositorio. Rotar tokens si aparecen en logs, commits o capturas.

## Riesgos residuales

- La protección contra abuso de formularios es rate limit; para campañas públicas conviene agregar CAPTCHA o un WAF de Cloudflare.
- La auditoría local necesita envío a un sistema externo para ser resistente a borrado del nodo.
- La validación de DNS reduce SSRF, pero en producción conviene además permitir únicamente dominios de media/CDN conocidos.
- La publicación real de Meta, SMTP y MongoDB requiere pruebas de permisos en cuentas propias antes de habilitarla.

# 10 · Estado actual y brechas

Este corte documenta el contraste de producto realizado el **26 de octubre de 2026**. Es un inventario operativo, no una promesa de que todas las capacidades estén completas.

## Lo que está comprobado

- La superficie pública responde en `https://afterstage.ar`.
- La API pública de agenda responde con eventos y fechas.
- Existen rutas públicas para notas, agenda, comunidad, red, servicios, seguros, marketplace, traslados y reemplazos.
- La API tiene health/readiness, persistencia Mongo, roles, permisos y auditoría.
- El flujo editorial distingue borrador, revisión y publicación.
- El sitemap excluye administración y contenido demo, e incluye rutas públicas de producto.
- El despliegue productivo se realiza mediante GitOps en el cluster `afterstage` de `underkode`; el cluster local no es producción.

## Brechas observadas

| Código | Brecha | Impacto | Cierre requerido |
| --- | --- | --- | --- |
| CONTENT-001 | La API pública no tiene notas publicadas | Notas queda vacía y el medio no demuestra su propuesta editorial | Cargar y revisar contenido real |
| MAIL-001 | Readiness indica `smtp: false` | Se pueden persistir hilos, pero no afirmar respuestas enviadas | Configurar SMTP, `reply-to`, remitente y prueba end-to-end |
| MEDIA-001 | R2/gateway no está habilitado como flujo productivo | Fotos y videos no tienen el circuito remoto definido | Configurar gateway, bucket, dominio, cuotas y secretos |
| BRAND-001 | La URL de Canva sigue pendiente | La identidad visual no tiene una fuente externa verificable | Recibir URL real y reemplazar `CANVA_URL_PENDIENTE` |
| DATA-001 | Directorio, fotógrafos, marketplace y coberturas públicas están vacíos | Las superficies existen, pero no tienen red ni oferta visible | Importar o moderar datos reales con consentimiento |

## Cómo informar un estado

Usar estas categorías en reportes, PRs y conversaciones:

- **Implementado:** existe código y prueba automatizada.
- **Publicado:** el código llegó a `main` y al rollout productivo.
- **Operativo:** además tiene datos reales, credenciales, responsables y una prueba end-to-end.
- **Bloqueado:** falta una decisión, proveedor, credencial o dato que no debe inventarse.

No usar “listo” para una ruta que solo responde 200. Informar implementación, publicación, operación y bloqueo por separado.

## Próxima verificación

1. Repetir `health`, `ready`, sitemap y rutas públicas después de cada rollout.
2. Confirmar al menos una nota real y un evento real de punta a punta.
3. Probar un email entrante y una respuesta real sin exponer credenciales.
4. Probar una subida de imagen a R2 y su lectura pública con cuota y MIME válidos.
5. Revisar visualmente desktop/mobile y consola antes de declarar cerrado el incremento.

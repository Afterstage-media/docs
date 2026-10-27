# 04 · Alcance y evolución del producto

Este documento separa lo que existe en la implementación de lo que está operativo y de lo que todavía requiere decisión, configuración o contenido real. Una ruta visible no equivale a una capacidad lista para prometer.

## Base implementada

- Shell público compartido con búsqueda, navegación y estados de carga/error/vacío.
- Notas y detalle de nota con borradores, publicación, canales, SEO, créditos y assets.
- Agenda con eventos, fechas múltiples, filtros, mapa y detalle vinculado.
- Comunidad, Red, Directorio y Reemplazos para perfiles, coberturas y postulaciones.
- Formularios de Seguros, Traslados, Marketplace y Servicios con estados internos.
- Operación para contenidos, prensa, usuarios, correo, plataforma e Instagram.
- API con roles, permisos, auditoría, rate limiting y validaciones de dominio.
- Sitemap, robots, health y readiness para operación y descubrimiento público.

## Capacidad que requiere operación real

| Capacidad | Qué falta para considerarla lista |
| --- | --- |
| Archivo editorial | Notas reales revisadas, publicadas y con créditos; no fixtures ni placeholders |
| Correo `@afterstage.ar` | Worker desplegado, webhook firmado, rutas verificadas y SMTP productivo |
| Fotos y video | Gateway desplegado, bucket/dominio R2, cuotas, secretos y política de retención |
| Marketplace | Aliados, catálogo, precios/leyendas, responsable y condiciones comerciales |
| Seguros | Productor o aseguradora responsable, productos vigentes y circuito de respuesta |
| Traslados | Proveedores, zonas, precios, disponibilidad y responsabilidad operativa |
| Directorio | Perfiles verificados, consentimiento de contacto y proceso de corrección |
| Instagram | Cuenta, permisos, credenciales, límites y criterio editorial de publicación |

## Próximos incrementos

### P0 · Confianza y contenido

1. Cargar el primer lote de notas y coberturas reales.
2. Verificar autores, fuentes, lugares, fechas, fotos y créditos.
3. Completar identidad de marca; reemplazar el placeholder de Canva por la URL real cuando sea entregada.
4. Revisar estados vacíos para que cada uno tenga una alternativa útil sin inventar actividad.

### P1 · Operación conectada

1. Habilitar correo de entrada y respuesta con credenciales productivas.
2. Integrar R2 de punta a punta y retirar dependencias de almacenamiento local para medios públicos.
3. Definir responsables, SLA y estados para seguros, traslados, marketplace y coberturas.
4. Agregar métricas operativas sin exponer datos personales.

### P2 · Crecimiento

1. Guardados, seguimiento de artistas/venues y alertas configurables.
2. Perfil y portfolio editables con moderación.
3. Checkout o patrocinio solo después de definir proveedor, facturación, reembolsos y términos.
4. Recomendaciones por ubicación, género y relación con eventos.

## Criterios de aceptación de un lanzamiento

- La documentación y la implementación nombran las mismas rutas y responsabilidades.
- Toda capacidad anunciada tiene datos reales, responsable y próximo paso.
- El contenido público no contiene fixtures, nombres inventados ni placeholders visibles.
- Los formularios no prometen contratación, seguro, pago o envío si la integración no está activa.
- Desktop, tablet y mobile no generan overflow horizontal ni pierden el CTA principal.
- Fechas de eventos mantienen el mismo día y hora entre API, Agenda, detalle y comunicaciones.
- `health`, `ready`, sitemap, logs, rollout y dominio público fueron verificados en `underkode`.

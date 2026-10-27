# 02 · Arquitectura de información

La arquitectura se organiza por intención, no por el rol interno de la cuenta. Una persona puede leer, colaborar, producir y operar con distintos permisos sin perder el contexto.

## Superficies públicas

| Superficie | Qué resuelve | Acción principal |
| --- | --- | --- |
| Inicio | Entender la propuesta y elegir una puerta de entrada | Explorar agenda o notas |
| Notas | Leer crónicas, entrevistas, columnas y coberturas | Leer la nota |
| Agenda | Descubrir shows, ferias, ciclos y encuentros por fecha, lugar o artista | Ver el evento |
| Comunidad | Conocer la red y participar | Ver perfiles |
| Red | Encontrar cobertura y conectar una necesidad con una persona | Buscar cobertura |
| Directorio | Consultar perfiles y datos verificados de la escena | Ver ficha |
| Servicios | Resolver una necesidad de producción | Pedir presupuesto |
| Seguros | Solicitar una cotización orientativa por producto y evento | Enviar solicitud |
| Marketplace | Consultar merch, servicios y beneficios aliados | Ver propuesta |
| Traslados | Resolver movilidad de personas y equipos | Pedir traslado |
| Reemplazos | Buscar quien cubra una fecha cuando la persona asignada no puede asistir | Buscar reemplazo |
| Política y créditos | Entender criterios, fuentes y reconocimiento | Leer reglas |

## Superficies de participación

- **Colaborá:** ingreso, perfil y presentación de trabajo.
- **Proponer contenido:** propuesta editorial que queda pendiente de revisión.
- **Foro del evento:** conversación vinculada a una fecha, sin mezclarla con la edición de una nota.
- **Postulaciones:** solicitud a una cobertura o búsqueda, con estado y contacto.
- **Perfil y portfolio:** identidad, ciudad, especialidad, muestras, disponibilidad y créditos.

## Superficies de operación

| Área | Responsabilidad |
| --- | --- |
| Contenidos | Borrador, revisión, publicación, retiro, canales, SEO y créditos |
| Prensa | Eventos, acreditaciones, coberturas, follow-ups y contactos |
| Correo | Ingreso, ruteo, hilos, reply-to y respuestas desde `@afterstage.ar` |
| Plataforma | Perfiles, solicitudes de seguro, postulaciones, traslados, marketplace y estados |
| Usuarios | Roles, permisos, activación y auditoría de acceso |
| Instagram | Conexión, permisos, publicación y métricas cuando la integración está habilitada |

## Recorridos principales

### Editorial colaborativo

1. Se propone una historia o se registra una cobertura.
2. La redacción valida datos, fuente, alcance y créditos.
3. Se crea un borrador; el agente puede asistir, pero no publica por sí solo.
4. Se revisa y publica en web, con imágenes y créditos.
5. La nota enlaza evento, perfiles y material relacionado cuando corresponde.

### Agenda a cobertura

1. Una persona descubre una fecha en Agenda.
2. Consulta detalle, ubicación, foro, Red o cobertura.
3. Una productora publica una necesidad con fecha, zona, presupuesto y contacto.
4. Una persona creadora se postula con perfil y muestra.
5. Operación actualiza estado, entrega y créditos.

### Evento a producción

1. La persona describe evento, producto y condiciones mínimas.
2. Afterstage registra una solicitud, no una contratación automática.
3. Operación deriva a proveedor, aseguradora o aliado responsable.
4. El estado y el próximo paso quedan visibles internamente.

### Correo editorial y operativo

1. Cloudflare Email Routing/Worker recibe el mensaje.
2. El webhook firmado valida origen y persiste el mensaje.
3. El ruteo crea o agrega el mensaje a un hilo.
4. Operación responde desde la bandeja con SMTP configurado.
5. Si SMTP no está listo, el sistema debe mostrar el bloqueo y no afirmar que envió.

### Fotos y medios

1. El frontend solicita una reserva al gateway.
2. El gateway valida identidad, cuota, MIME y destino.
3. El navegador sube directamente al bucket R2 mediante URL firmada.
4. La API persiste metadatos y la URL pública permitida.
5. Nunca se debe depender de una miniPC como almacenamiento público ni exponer secretos en el frontend.

## Entidades y relaciones

`evento → cobertura → perfil → postulación → entrega → crédito`

`nota → autoría/fuente → assets → canales → publicación`

`solicitud → hilo de correo → responsable → estado → próximo paso`

`cuenta → roles/permisos → auditoría → acceso a operación`

Los IDs de evento, nota, perfil y solicitud deben ser estables. Los estados de negocio deben ser explícitos y no inferirse solo por la existencia de una fecha o un email.

## Reglas de navegación

- La búsqueda global debe estar visible y declarar su alcance.
- Las rutas profundas conservan retorno contextual, filtros y consulta cuando sea posible.
- El shell público, el espacio de cuenta y la operación deben distinguirse.
- Una pantalla siempre comunica loading, vacío, error, éxito, permisos y siguiente paso.
- El sitemap solo incluye rutas públicas y contenido editorial publicado; no indexa administración, cuenta ni borradores.

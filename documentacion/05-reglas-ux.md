# 05 · Reglas UX

Estas reglas son el criterio común para diseñar, implementar y revisar Afterstage. La dirección visual se toma de [03 · Sistema visual e identidad de marca](./03-sistema-visual.md); estas reglas definen cómo debe comportarse esa identidad en una interfaz real.

## Principios

1. **La escena primero.** La interfaz debe ayudar a descubrir, leer, participar o trabajar. Cada pantalla tiene una acción principal reconocible.
2. **Cercanía sin ruido.** El tono puede ser informal y editorial, pero la navegación, los formularios y los estados del sistema deben ser directos.
3. **Continuidad.** Cambiar de sección no debe sentirse como abandonar el producto: el header, la búsqueda, la identidad y el contexto de navegación se mantienen estables.
4. **Contenido antes que decoración.** La estética de afiche refuerza jerarquía y señalética; no se usa para esconder estados vacíos, errores o acciones.

## Navegación y búsqueda

- La búsqueda global debe estar **visible, centrada y disponible** en el header. No se presenta únicamente como un botón de ícono.
- El campo debe tener label accesible, placeholder orientativo, foco visible y envío con Enter. El resultado debe reflejar la consulta en la URL para poder compartirlo y volver atrás.
- El header es un shell compartido: no se monta una copia distinta por página. Las rutas cambian el contenido central y conservan la navegación reutilizable.
- La sección activa se comunica con color, contraste y/o texto; nunca depende solamente del color.
- El menú móvil se abre y cierra con un control etiquetado, conserva el foco visible y ofrece una salida clara.
- Los enlaces deben describir su destino. Evitar etiquetas genéricas como “Más” o “Click acá” cuando se pueda nombrar la acción.

## Sidebar y espacio de trabajo

- El sidebar de escritorio permanece estable mientras se recorre el espacio de trabajo.
- En pantallas cortas, solo la lista de secciones hace scroll; encabezado y acciones de cuenta quedan disponibles.
- El scroll del sidebar debe ser discreto: barra fina, contraste suficiente, área de desplazamiento amplia y sin capturar el scroll de la página principal.
- Las secciones se agrupan por intención —consultar, trabajar, gestionar y cuenta— y no por orden de implementación.
- La opción activa debe ser evidente y mantener un target táctil de al menos 44 px en móvil.

## Estados y navegación entre rutas

- Loading, error, vacío y éxito son estados diseñados, con lenguaje humano y una acción de recuperación cuando corresponda.
- Cada estado debe responder: qué pasó, qué puede hacer la persona ahora y qué ocurrirá después.
- Un estado vacío no debe simular actividad ni inventar contenido. Debe ofrecer una alternativa útil o explicar qué falta para que aparezca información.
- Al cambiar de ruta, se actualiza solo el contenido que cambió. No se simula una recarga completa ni se desmonta el shell compartido.
- Las solicitudes pertenecen a la pantalla que las necesita; una respuesta lenta no debe pisar datos de otra ruta o filtro.
- Las transiciones deben respetar `prefers-reduced-motion` y no bloquear la lectura.

## Formularios y confianza

- Pedir solo los datos necesarios para la intención actual; el perfil completo puede completarse después.
- Cada control tiene label visible, ayuda contextual y error junto al campo; el placeholder no reemplaza al label.
- Explicar quién verá un dato sensible y para qué se solicita.
- Después del envío, diferenciar propuesta, solicitud, cotización, contratación, pago y publicación.
- No afirmar que se envió un correo, se contrató un seguro, se reservó un traslado o se subió una foto si la integración está bloqueada.
- Conservar los valores válidos y ofrecer referencia, estado y próximo paso.

## Agenda, fechas y medios

- La fecha mostrada debe ser la fecha calendario del evento en su sede; nunca debe correrse por una conversión accidental de medianoche UTC.
- Agenda, detalle del evento, Traslados, Reemplazos y comunicaciones deben mostrar el mismo día, hora y rango.
- Si la hora no está confirmada, mostrar “fecha/hora a confirmar” en lugar de inventarla.
- Una foto o video debe mostrar crédito, origen y estado de publicación; el almacenamiento público no depende de una computadora personal.

## Público, cuenta y operación

- El sitio público privilegia explorar y leer sin registro.
- Mi espacio explica qué puede hacer la cuenta y qué permisos tiene.
- Operación muestra contexto, estado, responsable, errores y próximo paso; no expone secretos ni datos innecesarios.
- Las rutas privadas no deben aparecer como contenido indexable del sitemap.
- Los permisos se comunican con lenguaje claro: sin acceso, pendiente de revisión, archivado o publicado.

## Responsive y accesibilidad

- Diseñar primero la jerarquía del contenido y luego adaptar la composición a desktop, tablet y móvil.
- No debe existir scroll horizontal accidental. Los controles, enlaces y botones deben poder usarse con una mano.
- Si una tabla no puede convertirse en tarjetas, el scroll horizontal debe estar contenido en su propio wrapper, ser enfocable y explicar cómo desplazarse.
- Validar como mínimo 1920×1080, 768×1024 y 375×812, incluyendo estados vacíos y errores.
- Cada control tiene nombre accesible, foco visible y estado comunicable por teclado y lector de pantalla.
- Contraste, tamaño de texto y estados de error deben poder entenderse sin depender del color, el movimiento o una imagen.
- El contenido principal debe conservar gutters consistentes y no quedar pegado al borde del viewport.

## Criterio de aceptación para cada cambio UX

Antes de dar por terminado un cambio, revisar:

- ¿La acción principal se entiende en cinco segundos?
- ¿La búsqueda sigue visible y usable en desktop y móvil?
- ¿El cambio de ruta conserva header, sidebar y contexto?
- ¿El scroll del sidebar es contenido y accesible?
- ¿Se validaron loading, error, vacío, éxito y foco?
- ¿Las fechas conservan día y hora en todos los puntos del flujo?
- ¿La pantalla evita inventar contenido, estados o confirmaciones?
- ¿Se revisaron los permisos y la exposición de datos?
- ¿La solución respeta [la identidad de marca](./03-sistema-visual.md#identidad-de-marca)?

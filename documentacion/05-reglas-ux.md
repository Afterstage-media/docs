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
- Al cambiar de ruta, se actualiza solo el contenido que cambió. No se simula una recarga completa ni se desmonta el shell compartido.
- Las solicitudes pertenecen a la pantalla que las necesita; una respuesta lenta no debe pisar datos de otra ruta o filtro.
- Las transiciones deben respetar `prefers-reduced-motion` y no bloquear la lectura.

## Responsive y accesibilidad

- Diseñar primero la jerarquía del contenido y luego adaptar la composición a desktop, tablet y móvil.
- No debe existir scroll horizontal accidental. Los controles, enlaces y botones deben poder usarse con una mano.
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
- ¿La solución respeta [la identidad de marca](./03-sistema-visual.md#identidad-de-marca)?

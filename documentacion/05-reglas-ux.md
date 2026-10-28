# 05 · Reglas UX

Estas reglas son normativas. Definen cómo debe comportarse Afterstage cuando se diseña, implementa o revisa una interfaz.

La dirección visual se toma de [03 · Sistema visual e identidad de marca](./03-sistema-visual.md). La marca define el tono, la tensión editorial y los recursos visuales; estas reglas definen cómo convertir esa identidad en una experiencia cómoda, clara, accesible y confiable.

La evidencia de auditorías, hallazgos y prioridades debe vivir en documentos separados. Este archivo no es un reporte: es la guía de diseño y aceptación.

## 1. Principios rectores

### 1.1 La escena primero

La interfaz debe ayudar a descubrir, leer, participar o trabajar. Cada pantalla debe tener una acción principal reconocible.

### 1.2 La intención antes que el rol

La persona no debería tener que elegir primero un rol técnico. Primero debe poder expresar qué quiere hacer:

- Descubrir un show o una historia.
- Participar o aportar.
- Cubrir, crear o colaborar.
- Mover un proyecto o evento.
- Contratar una solución.
- Ofrecer un servicio.
- Operar Afterstage.

Una misma cuenta puede tener varios perfiles: fotógrafo, manager, artista, medio, venue o proveedor.

### 1.3 Cercanía sin ruido

El tono puede ser informal y editorial, pero la navegación, los formularios, los errores y los estados deben ser directos. La personalidad nunca debe ocultar qué puede hacer la persona.

### 1.4 Contenido antes que decoración

La estética de afiche refuerza jerarquía y señalética; no se usa para esconder estados vacíos, errores, falta de contenido o acciones importantes.

### 1.5 Una pantalla, una promesa principal

El título, la explicación, la acción principal y el resultado esperado deben hablar de la misma tarea. Si una pantalla promete cotizar, no debe presentar un botón que parezca cobrar sin explicar el cambio.

### 1.6 La acción principal en cinco segundos

En los primeros segundos deben poder responderse tres preguntas:

1. ¿Dónde estoy?
2. ¿Qué puedo hacer acá?
3. ¿Qué pasa si toco el botón principal?

## 2. Identidad de marca aplicada a UX

La identidad es **cartelera de barrio + revista independiente**: tensión editorial, señalética, cercanía y claridad.

### 2.1 Usar la identidad para orientar

- Marfil #F4F0E8: superficie principal cálida y legible.
- Tinta #171717: texto, navegación y contraste.
- Coral #FF5C47: acción y acento principal.
- Azul eléctrico #3155FF: enlaces, categorías y foco.
- Verde lima #C7F36A: estados positivos y beneficios.
- Space Grotesk: display y titulares.
- DM Sans: texto y lectura.
- Etiquetas en mayúsculas: señalética y clasificación.

### 2.2 No convertir la estética en ruido

- No usar textura, color o movimiento como sustituto de jerarquía.
- No usar un color como única forma de comunicar estado.
- No crear una tarjeta decorativa sin acción, dato o contexto.
- No sacrificar legibilidad por una composición editorial.
- No hacer que un título grande desplace la acción importante fuera del primer viewport.
- Mantener bordes negros finos y radios pequeños cuando aporten estructura, no por repetición automática.

### 2.3 Regla de consistencia de marca

Toda modificación de color, tipografía, logo, recurso gráfico o patrón de composición debe revisarse contra el sistema visual y estas reglas UX. Si cambia una regla de marca, se actualizan ambos documentos.

## 3. Arquitectura de información y navegación

### 3.1 Organizar por intención

La navegación visible debe agrupar las rutas por trabajos que las personas quieren realizar:

| Entrada de intención | Contenido |
|---|---|
| Explorar | Notas, Agenda, mapa y detalle de eventos |
| Participar | Comunidad, Colaborador, Publicar y Créditos |
| Trabajar en la escena | Red, Directorio y Reemplazos |
| Resolver un evento | Servicios, Contratar, Seguros y Traslados |
| Comprar y apoyar | Marketplace, merch y beneficios |
| Mi espacio | Perfil, postulaciones, propuestas, accesos y conversaciones |
| Operación | Administración, prensa, contenidos, usuarios y plataforma |

Las rutas existentes pueden conservarse para enlaces, SEO y compatibilidad, pero la presentación debe usar lenguaje de intención.

### 3.2 Entrada por intención en la Home

La portada debe ofrecer una puerta de entrada clara para:

- Quiero descubrir.
- Quiero leer o aportar.
- Quiero colaborar.
- Quiero mover mi proyecto o evento.
- Quiero contratar.
- Quiero ofrecer mi trabajo.

No se debe forzar el registro antes de que una persona pueda explorar contenido público.

### 3.3 Shell compartido

- El header es un shell compartido y no una copia distinta por página.
- Las rutas cambian el contenido central y conservan navegación, identidad y contexto.
- El sitio público, Mi espacio y Operación deben distinguirse visualmente.
- El usuario debe reconocer siempre en qué contexto está trabajando.
- La sección activa debe comunicarse con texto, contraste, estructura o color; nunca solo con color.
- Las rutas profundas deben ofrecer retorno contextual o breadcrumb.
- Volver debe conservar, cuando sea posible, filtros, búsqueda y selección anterior.

### 3.4 Búsqueda

- La búsqueda global debe estar visible, disponible y tener nombre accesible.
- Debe permitir envío con Enter y foco visible.
- El alcance debe estar explícito: notas, eventos, perfiles, servicios o todo Afterstage.
- La consulta y los filtros deben reflejarse en la URL cuando sea útil compartir o volver atrás.
- Los resultados deben informar qué tipo de contenido se encontró.
- Un resultado vacío debe ofrecer una alternativa concreta.

### 3.5 Menú móvil

- El menú se abre y cierra con un control etiquetado.
- El control comunica su estado con aria-expanded.
- Al abrirse, el foco entra al menú; al cerrarse, vuelve al control que lo abrió.
- Debe existir una salida clara.
- Los targets de navegación deben medir al menos 44 px.
- El menú no debe capturar el scroll de la página principal de forma inesperada.

## 4. Jerarquía visual y componentes

### 4.1 Botones y CTAs

Los botones deben usar verbos concretos:

| Intención | CTA preferida |
|---|---|
| Leer | Leer la nota |
| Ver un evento | Ver el evento |
| Participar | Enviar aporte |
| Postularse | Postularme |
| Buscar una persona | Buscar perfiles |
| Ofrecer trabajo | Ofrecer mi trabajo |
| Pedir cobertura | Necesito cubrir una fecha |
| Pedir presupuesto | Pedir presupuesto |
| Enviar solicitud | Enviar solicitud |
| Publicar | Publicar una fecha o Publicar una búsqueda |
| Corregir datos | Corregir esta ficha |

- Una pantalla debe tener una CTA primaria.
- Las CTAs secundarias no deben competir visualmente con la principal.
- “Continuar al pago” solo debe usarse cuando el siguiente paso sea realmente un pago.
- Toda CTA debe anticipar el resultado, no solo nombrar la navegación.
- Un botón deshabilitado debe explicar qué falta para habilitarlo.

### 4.2 Cards y contenido clickeable

- Una card interactiva debe tener affordance visible: CTA, enlace, icono o estado de foco.
- El click en toda la card puede funcionar como atajo, pero no debe ser la única forma de descubrir que es interactiva.
- Las cards deben mostrar el dato que permite decidir: fecha, lugar, precio, disponibilidad, estado o categoría.
- No usar una card solo como decoración.

### 4.3 Estados

Toda ruta y acción debe diseñar sus estados:

- loading;
- vacío;
- error;
- éxito;
- deshabilitado;
- sin permisos;
- sin verificar;
- guardado;
- pendiente;
- confirmado.

Cada estado debe responder:

1. Qué pasó.
2. Qué puede hacer ahora la persona.
3. Qué ocurrirá después.

### 4.4 Fechas y horas

- Mostrar siempre la fecha local del evento o sede.
- Mantener el mismo día y hora en API, Agenda, detalle, Traslados y comunicaciones.
- Evitar conversiones accidentales de medianoche UTC.
- Incluir zona horaria cuando el contexto lo necesite.
- Usar un formato consistente por producto y región.
- En formularios, explicar si la fecha refiere a inicio, fin o fecha de publicación.

## 5. Formularios

### 5.1 Mínimo necesario

Cada campo debe justificar su existencia para la tarea actual. El primer paso no debe pedir un perfil completo si basta con una solicitud breve.

| Flujo | Primer paso |
|---|---|
| Proponer historia | Título, idea, fecha/evento y contacto |
| Crear perfil de fotógrafo | Nombre, ciudad, especialidad, un portfolio y contacto |
| Buscar cobertura | Fecha, evento, necesidad, presupuesto y contacto |
| Pedir seguro | Producto, fecha, ciudad y tipo de evento |
| Pedir traslado | Evento, origen, pasajeros y contacto |
| Contratar servicio | Servicio, objetivo, fecha, proyecto y contacto |

### 5.2 Divulgación progresiva

Los formularios largos deben dividirse en:

1. Intención.
2. Datos mínimos.
3. Datos específicos de la solución.
4. Contacto y confirmación.
5. Perfil completo, portfolio o documentación posterior.

Usar pasos, resumen de avance, guardado parcial y posibilidad de continuar más tarde.

### 5.3 Agrupación

Separar visual y semánticamente:

- Datos del evento.
- Necesidad o producto.
- Disponibilidad y condiciones.
- Datos de contacto.
- Consentimiento y documentación.

No mezclar información legal con preguntas de contexto sin explicar el motivo.

### 5.4 Labels y ayuda

- Cada control tiene un label visible.
- No depender solo del placeholder.
- Los labels permanecen visibles cuando el campo está completo.
- Los ejemplos explican formato, cantidad, URL o archivo esperado.
- Los campos ambiguos deben cambiar de nombre o mostrar ayuda.
- Todo campo sensible debe explicar para qué se solicita el dato y quién lo verá.

### 5.5 Validación y errores

- Validar antes de enviar cuando sea posible.
- Mostrar el error junto al campo.
- Explicar cómo corregirlo.
- No depender solo del color.
- Conservar los valores válidos ya escritos.
- Llevar el foco al primer error sin desplazarlo detrás del header.
- No reiniciar el formulario completo por un error puntual.
- Evitar envíos duplicados mientras la solicitud está procesándose.

### 5.6 Envío y confirmación

Después de enviar:

- Confirmar que la solicitud fue recibida.
- Mostrar referencia o estado si existe.
- Explicar tiempo estimado de respuesta.
- Informar el próximo paso.
- Ofrecer enlace a conversación, estado o retorno útil.
- Diferenciar consulta, solicitud, cotización y pago.

### 5.7 Controles táctiles

- Inputs, selects y botones principales deben medir al menos 44–48 px de alto.
- Debe existir espacio suficiente entre controles.
- La CTA debe ser alcanzable con una mano.
- El teclado virtual no debe ocultar el campo activo ni el mensaje de error.
- La consistencia táctil debe mantenerse en foro, traslados, filtros, Red, Seguros y Contratar.

## 6. Responsive y mobile

- Diseñar primero la jerarquía y luego adaptar la composición.
- Probar desktop 1920×1080, tablet 768×1024 y mobile 375×812.
- No debe existir overflow horizontal accidental del body.
- Las tablas deben convertirse en cards o tener scroll interno controlado.
- El contenido principal debe conservar gutters consistentes.
- Los títulos no deben quedar cortados ni tapados por el header.
- Usar scroll-padding-top y scroll-margin-top para header fijo y anclas.
- Las listas largas deben tener búsqueda, filtros, agrupación o paginación.
- Las acciones principales no deben requerir recorrer miles de píxeles.
- La interfaz debe funcionar con una mano y sin precisión motora fina.

### 6.1 Sistema de contenedores y anchos

- Todas las páginas públicas deben usar un único contenedor horizontal de referencia: `--content-width`.
- El hero puede ocupar el ancho completo como superficie visual, pero su texto, filtros y acciones deben alinearse con el mismo gutter del contenido que sigue.
- No mezclar en páginas públicas heroes de `1180px`, ancho completo o gutters propios sin una justificación documentada.
- El ancho de lectura debe seguir `--reading-width` o `--text-width`; no crear medidas ad hoc para cada ruta.
- Las excepciones —por ejemplo, una galería, un mapa o un canvas editorial— deben ampliar solo el bloque que necesita amplitud, no desplazar toda la página.
- La comparación mínima entre rutas hermanas es: inicio del hero, inicio del título, ancho del título, inicio del primer bloque operativo y gutter lateral.
- Un cambio de ancho en un componente compartido se valida contra Notas, Agenda, Marketplace, Seguros, Traslados, Servicios y Contratar antes de aprobarse.

## 7. Accesibilidad

Estas reglas toman WCAG 2.2 AA como referencia de diseño y validación. No implican por sí solas una certificación formal.

### 7.1 Teclado y foco

- Todo control debe ser accesible con teclado.
- El foco debe ser visible y tener contraste suficiente.
- El orden de foco debe seguir el orden visual y la tarea.
- No debe existir foco atrapado sin una salida clara.
- Los anclajes no deben dejar el foco detrás del header.
- Debe existir skip-link al contenido principal.

### 7.2 Nombre y semántica

- Cada input, select, botón y enlace debe tener nombre accesible.
- Los iconos de buscar, cerrar, volver y menú deben tener etiqueta.
- Los headings deben seguir una jerarquía lógica.
- Las regiones principales deben usar landmarks semánticos.
- Las tablas deben tener encabezados comprensibles.
- El texto del enlace debe describir su destino.

### 7.3 Color, contraste y movimiento

- La información no debe depender solo del color.
- El texto y los controles deben tener contraste suficiente.
- Los estados de error, selección y éxito deben tener texto o estructura adicional.
- Respetar prefers-reduced-motion.
- No usar movimiento para transmitir información indispensable.
- No permitir animaciones que bloqueen lectura o interacción.

## 8. Confianza, privacidad y seguridad UX

- Explicar qué datos se piden, por qué y quién los verá.
- Pedir datos sensibles solo cuando sean necesarios.
- Confirmar antes de revocar accesos, borrar contenido o descartar cambios.
- Mostrar claramente qué conexión, perfil o proyecto se está modificando.
- Separar permisos públicos, personales y de operación.
- Proteger rutas privadas antes de renderizar su contenido.
- Un usuario sin permiso debe recibir una respuesta clara y recuperable.
- Un 404 debe ser útil y no dejar errores de runtime.
- Una petición fallida no debe destruir los datos ingresados.
- Las acciones de pago deben informar monto, proveedor y momento del cobro antes de confirmar.

## 9. Contenido y tono

- Mantener cercanía antes que solemnidad.
- Escribir como una plataforma de la escena, no como un panel técnico.
- Usar frases cortas y concretas.
- Escribir para escaneo: títulos informativos, listas, labels y resúmenes.
- Evitar abstracciones como “Gestionar” cuando se pueda nombrar la acción real.
- No usar “Más”, “Continuar” o “Click acá” sin contexto suficiente.
- El contenido patrocinado debe identificarse con transparencia.
- Los créditos deben ser visibles y respetar a quienes producen una pieza.
- La política editorial y las reglas de comunidad deben ser fáciles de encontrar.

## 10. Rendimiento y resiliencia percibida

- La primera pantalla debe mostrar valor y una acción antes de cargar módulos secundarios.
- No presentar una pantalla vacía mientras llegan datos.
- Diferenciar loading de “no hay resultados”.
- Mostrar skeleton o mensaje contextual cuando la carga tarda.
- Permitir reintentar una búsqueda o petición fallida.
- Aislar el fallo de una sección para no romper todo el shell.
- No permitir que una respuesta lenta de una ruta pise los datos de otra.
- Mantener datos de formulario ante errores de red.
- Evitar listas extensas sin filtros, agrupación o paginación.

## 11. Checklist de aceptación para cada cambio UX

Antes de aprobar una pantalla o flujo, verificar:

- [ ] La intención de la persona se entiende en cinco segundos.
- [ ] Existe una sola CTA primaria y describe el resultado.
- [ ] El lenguaje corresponde al mundo real del usuario.
- [ ] La pantalla tiene loading, vacío, error, éxito y sin permisos cuando corresponda.
- [ ] Los formularios piden solo el mínimo necesario.
- [ ] Los campos sensibles explican su propósito.
- [ ] Los controles principales miden al menos 44–48 px.
- [ ] Los errores son específicos, visibles y recuperables.
- [ ] El envío confirma qué ocurrió y qué sigue.
- [ ] No hay overflow horizontal en 1920, 768 ni 375 px.
- [ ] El header fijo no tapa contenido ni foco.
- [ ] El foco es visible y el orden de teclado es lógico.
- [ ] La información no depende solo del color.
- [ ] La solución respeta el sistema visual y la identidad de marca.
- [ ] La ruta funciona para el perfil que realmente la necesita.
- [ ] El cambio tiene evidencia reproducible y una prueba de regresión.

## 12. Documentos relacionados

- [01 · Visión del producto](./01-vision.md)
- [02 · Arquitectura](./02-arquitectura.md)
- [03 · Sistema visual e identidad de marca](./03-sistema-visual.md)
- [04 · MVP](./04-mvp.md)
- [10 · Protocolo de auditoría UX por patrones](./10-protocolo-auditoria-ux-por-patrones.md)

## 13. Regla de auditoría transversal

Cuando se detecta un problema en una pantalla, no alcanza con corregir esa instancia. Hay que identificar el patrón que lo produce, inventariar sus apariciones, revisar sus estados y repetir la prueba en todas las rutas y viewports afectados.

La auditoría debe dejar evidencia de:

- el hallazgo original y su patrón generalizado;
- todas las rutas y componentes equivalentes;
- los estados loading, vacío, error, éxito y permisos que correspondan;
- desktop, tablet y mobile cuando la superficie los soporte;
- la entrada, interacción y salida de la ruta;
- la corrección aplicada en el nivel compartido más alto posible;
- la regresión posterior y los casos todavía no cubiertos.

El protocolo detallado está en [10 · Protocolo de auditoría UX por patrones](./10-protocolo-auditoria-ux-por-patrones.md).

### 13.1 Regla de shell según sesión

- Una sesión activa conserva el header y el menú del espacio de trabajo en todas las rutas, incluidas las páginas de contenido público.
- El estado de autenticación, no la URL visitada, define el shell principal.
- Las acciones de postulación y administración deben tener nombres distintos y orientados a la tarea.
- Cada auditoría debe probar una ruta representativa como visitante y con sesión activa para detectar cambios de navegación inesperados.

## 14. Comodidad humana, proporción y jerarquía

Estas reglas son obligatorias para no confundir una interfaz técnicamente estable con una interfaz cómoda para una persona real.

### 14.1 La primera tarea antes que la portada

- Toda página de utilidad debe mostrar su primera decisión o acción dentro del primer viewport, o explicar explícitamente por qué la lectura introductoria es necesaria.
- Una portada editorial puede tener impacto, pero no debe ocultar la búsqueda, el filtro, el formulario, la agenda o el CTA que justifica la página.
- Si la acción principal queda por debajo de un viewport completo en mobile o de aproximadamente 900 px de recorrido en desktop, revisar la composición antes de aprobar.
- El primer control interactivo que aparece debe ser el que ayuda al objetivo principal, no un retorno, una decoración o un enlace secundario.

### 14.2 Escala del hero

- En páginas de tarea, el hero debe ser compacto: el título no debería superar cinco líneas en desktop ni ocupar más de aproximadamente la mitad del primer viewport sin una acción asociada.
- En mobile, dividir titulares extensos o reducir su escala cuando obliguen a recorrer la pantalla antes de entender la acción.
- La escala tipográfica debe reforzar la jerarquía, no competir con el formulario, los filtros o los resultados.
- La excepción editorial debe justificarse por objetivo de marca y conservar una entrada temprana a la tarea.

### 14.3 Proporción y espacio útil

- El espacio vacío debe separar, agrupar o dar descanso; no debe existir solo porque el layout dejó una columna sin función.
- Un formulario o panel operativo debe estar contenido visualmente y tener una relación clara entre título, ayuda, campos, estado y CTA.
- No ubicar una tarea estrecha a un extremo de una pantalla ancha dejando un vacío dominante del otro lado sin contenido equivalente.
- La proporción se valida con contenido vacío, contenido real y error; una tarjeta equilibrada solo en un estado no alcanza.

### 14.4 Formularios cómodos

- El primer paso debe pedir lo mínimo necesario para iniciar una conversación o solicitud.
- Si un formulario necesita más de una pantalla de lectura, dividirlo por intención y mostrar progreso, resumen y próximo paso.
- La CTA del primer paso debe estar visible sin recorrer una pared de campos o una introducción repetida.
- Cada grupo debe tener un título que explique su propósito y no mezclar contexto, datos legales y contacto sin motivo.
- No repetir el nombre del servicio como titular y como bloque principal si la repetición no ayuda a decidir.
- Una persona debe poder revisar qué está solicitando antes de enviar; “Continuar” debe explicar hacia dónde continúa.

### 14.5 Decoración con presupuesto de atención

- Cada página puede tener identidad visual, pero la decoración tiene un presupuesto de atención limitado.
- Un ticker, marquee, estrella, reflector o textura no debe repetir información útil, distraer durante la carga de datos ni competir con la CTA.
- No duplicar un recurso decorativo en la misma pantalla salvo que cumpla una función de orientación diferente.
- El movimiento debe detenerse o reducirse con `prefers-reduced-motion` y nunca ser necesario para comprender la tarea.

### 14.6 Lectura y escaneo

- El cuerpo de lectura debe mantenerse en una medida cómoda, aproximadamente entre 55 y 80 caracteres por línea en desktop.
- Páginas largas de política, créditos o explicación deben ofrecer subtítulos, índice o navegación interna cuando el contenido supere varios viewport.
- Los párrafos deben tener suficiente interlineado y separación; no usar el tamaño display para el cuerpo.
- La información más importante debe poder encontrarse por títulos, labels, listas y resúmenes sin leer cada palabra.

### 14.7 Regla de decisión para auditorías

Una página no se aprueba solo porque:

- no tenga overflow horizontal;
- tenga todos los controles presentes;
- responda HTTP 200;
- no muestre errores de consola;
- tenga una estética consistente.

Se aprueba cuando una persona puede orientarse, entender la promesa, iniciar la tarea, completar los datos necesarios y recuperarse de un error sin esfuerzo desproporcionado.

## 15. Registro humano mínimo por pantalla

Toda auditoría futura debe registrar, como mínimo:

- objetivo principal de la persona;
- primera acción útil y coordenada/posición aproximada;
- altura y líneas del hero;
- inicio y fin del formulario o bloque operativo;
- cantidad de decisiones antes de la CTA;
- espacios vacíos que no cumplen una función;
- elementos decorativos que compiten por atención;
- puntaje de orientación, proporción, densidad, comodidad y confianza;
- estado visitante, sesión activa y rol relevante;
- desktop, tablet y mobile;
- hallazgo equivalente en otras rutas.

El [Checklist humano completo](../../Analisis%20UX%20Afterstage%202026-10-26/00-checklist-humano-main269.md) y la [auditoría humana de `main-269`](../../Analisis%20UX%20Afterstage%202026-10-26/09-auditoria-humana-completa-main269.md) muestran la aplicación de estas reglas.

## 16. Componentes compartidos como regla de calidad

La consistencia no debe depender de que cada página recuerde copiar el mismo CSS y la misma lógica. Todo patrón repetido debe tener un componente reutilizable y una única fuente de verdad.

### 16.1 Componentes obligatorios

- `PageTitle` para eyebrow, título, descripción, acción y contenedor del hero.
- `SectionHeading` para títulos de secciones y enlaces de contexto.
- `FormField`, `TextField`, `TextAreaField` y `SelectField` para labels, ayuda, campos y medidas táctiles.
- `FormSection` para fieldsets con título y explicación.
- `FormProgress` para formularios de varios pasos.
- `FormActions` para volver, continuar, enviar y estados de carga.
- Componentes de estado para carga, vacío, error y éxito.

### 16.2 Regla de implementación

- Una página no debe crear una variante local de estos patrones si el componente compartido puede resolverla mediante props.
- Si una excepción visual o de interacción es necesaria, debe tener nombre, test y justificación de objetivo.
- Los componentes compartidos definen semántica, accesibilidad, spacing, foco, error y responsive; las páginas aportan contenido y comportamiento de negocio.
- Una corrección aplicada a un componente compartido debe validarse en todas las rutas que lo consumen.
- Una pantalla nueva no se aprueba si repite manualmente un hero, un campo, un progreso o un bloque de acciones existente.

### 16.3 Criterio de revisión

Durante una revisión, buscar primero el componente compartido que debería controlar el problema. Si el mismo hallazgo aparece en dos rutas, deja de ser un ajuste local y pasa a ser una corrección del componente o del token global.

# Agenda de próximos eventos

La ruta `/agenda` de la SPA React combina los eventos editoriales cargados desde el panel
de prensa con fuentes RSS/Atom externas. El backend consulta las fuentes cada
cinco minutos y descarta fechas pasadas, URLs no HTTPS y destinos privados.

## Fuentes investigadas

- La agenda cultural del Gobierno de la Ciudad de Buenos Aires es un sitio web
  dinámico y no expone un RSS estable público.
- Eventbrite publica listados web dinámicos; su búsqueda no ofrece un RSS
  confiable para consumo sin autenticación.
- Bandsintown y Songkick tienen datos útiles, pero requieren API/app key para un
  uso automatizado y no deben scrapearse.

Por eso la integración usa RSS/Atom genérico y permite conectar una fuente
oficial cuando el organizador o la sala la provea. También se pueden seguir
cargando eventos manualmente desde `/admin/prensa`.

## Configuración

En `backend/.env`:

```dotenv
EVENTS_RSS_URLS=https://ejemplo.org/agenda.xml,https://otra-sala.org/feed
```

Las entradas se normalizan a nombre, artista, sala, ciudad, fecha y enlace; se
deduplican y se muestran junto a los eventos propios del medio. Una fuente caída
no interrumpe la agenda local.

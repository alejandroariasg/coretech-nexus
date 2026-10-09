# CoreTech Nexus — Landing Page

## Qué es esto

Landing page de **CoreTech Nexus**, empresa de soluciones informáticas (software y hardware). El sitio está actualmente en estado de **"sitio en mantenimiento"**: una sola página que muestra el logo, un mensaje de mantenimiento y los datos de contacto, mientras el sitio completo no está construido.

## Estructura

```
landingpage/
├── index.html   # Página completa: HTML + CSS + JS en un solo archivo autocontenido
└── logo.png     # Logo original de la empresa (323×103px, con transparencia)
```

No hay build step, framework ni dependencias de paquetes. `index.html` es estático y autosuficiente: solo carga tipografías desde Google Fonts por red; todo lo demás (estilos, script del fondo animado, logo) está embebido en el propio archivo.

- El logo va embebido como `data:image/png;base64,...` dentro del `<img>` del `.logo-plate` (no se referencia `logo.png` desde el HTML; ese archivo es la copia de respaldo del original).

## Contenido / datos de contacto

- Correo: `gerencia@coretech-nexus.com`
- Teléfono: `+57 312 715 3432`
- Mensaje principal: "Sitio en mantenimiento"

Si cambia cualquiera de estos datos, están hardcodeados directamente en el HTML (buscar `mailto:` y `tel:` en `index.html`).

## Sistema de diseño

Tema **oscuro fijo** (no hay modo claro/oscuro alternable) — es una decisión deliberada: la página está pensada como un panel de diagnóstico/consola técnica, coherente con una empresa de software y hardware.

**Tipografía** (Google Fonts):
- Display: `Chakra Petch` (títulos, wordmark) — carácter angular/técnico
- Cuerpo: `IBM Plex Sans`
- Datos/mono: `IBM Plex Mono` (contacto, estado, labels)

**Paleta** (variables CSS en `:root`):
- `--bg: #0A0E13`, `--bg-2: #0E141C` — fondo casi negro con sesgo azulado
- `--panel: #10161F` / `--panel-border: #1E2A37` — panel central
- `--accent: #3FE0D0` (cian) — color de marca de la página (estado, enlaces, glow)
- `--accent-2: #FF8F4C` (ámbar) — acento secundario, uso mínimo
- `--text: #E7EEF5`, `--muted: #7E8FA3`, `--muted-dim: #4D5C6E`

**Logo**: el logo real de la empresa usa texto azul marino oscuro que no se lee bien sobre el fondo oscuro de la página. Por eso se muestra dentro de una "placa" clara (`.logo-plate`, gradiente blanco → gris muy suave) con un halo cian sutil — así se conserva el logo sin alterar sus colores de marca.

**Fondo animado**: `<canvas id="net">` dibuja una red de nodos/líneas sutil (estilo circuito) vía JS, respeta `prefers-reduced-motion`.

## Convenciones a mantener

- Mantener el archivo **autocontenido** (sin build step) mientras el sitio siga siendo solo esta landing de mantenimiento.
- No introducir modo claro — el diseño está pensado como experiencia oscura única.
- Cualquier adición de contenido debe respetar la paleta y tipografías ya definidas arriba, no mezclar otras fuentes/colores.

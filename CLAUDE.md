# CLAUDE.md

Este archivo proporciona orientación a Claude Code (claude.ai/code) al trabajar con el código de este repositorio.

## Descripción General

Este es un **sitio HTML estático puro** para Nívisix Soluciones — sin sistema de build, sin gestor de paquetes y sin paso de compilación. Los archivos se sirven directamente tal como están (diseñado para GitHub Pages).

## Desarrollo Local

Abre cualquier archivo `.html` directamente en el navegador, o sirve la raíz con cualquier servidor de archivos estáticos:

```powershell
# Python (si está instalado)
python -m http.server 8080

# Node (si está instalado)
npx serve .
```

No existen comandos de build, lint ni pruebas.

## Arquitectura

### Páginas
- `index.html` — Página principal de la empresa (Nívisix Soluciones)
- `finanzas-en-accion.html` — Landing page del curso de educación financiera
- `finanzas-hari-om.html` — Segunda página de curso financiero
- PDFs (`computadoras.pdf`, `finanzas.pdf`, `FINANZAS-HARIOM.pdf`) — Contenido descargable

Cada página es autocontenida: importa su propio CSS/JS al final y usa la grilla de Bootstrap 3 para el layout. Las secciones dentro de cada página son bloques `<div id="...">` con anclas; la barra de navegación fija usa scroll suave para navegar entre ellas.

### Organización de Assets
- `assets/css/` — Estilos personalizados; `style.css` es la hoja principal, `media-queries.css` maneja los breakpoints, `buttons.css` / `form-elements.css` son sobrescrituras específicas
- `assets/js/scripts.js` — Todo el JS personalizado: navegación con scroll-spy, menú móvil, dropdowns con Select2, grilla Masonry para el portafolio, inicialización de Google Maps, animaciones de labels en el formulario de contacto
- `assets/bootstrap/` — Bootstrap 3 (CSS + JS + Glyphicons); no actualizar sin probar todas las páginas
- `assets/js/` — jQuery 1.10.2 más plugins (Masonry, Select2, Magnific Popup, Backstretch, EmailJS)
- `assets/fonts/` — Tipografía Signika (formatos webfont)
- `assets/img/` — Organizado en `icons/`, `portfolio/`, `team/`, `slider/`; variantes retina usan el sufijo `@2x`

### Integraciones de Terceros
- **EmailJS** — Los envíos del formulario de contacto van a `nivisix.soluciones@gmail.com` mediante el servicio `service_gc4pvxe` / plantilla `template_yzr484j` (son claves públicas del lado del cliente, no secretos)
- **Google Analytics** — ID de seguimiento `G-3ZWR725QH8`
- **Google Maps API** — Cargado por HTTP; las coordenadas del mapa en `scripts.js` están hardcodeadas (actualmente apuntan a Nueva York, no a la ubicación del negocio)

### Flujo de Inscripción a Cursos
`finanzas-en-accion.html` y `finanzas-hari-om.html` leen un parámetro `ref` de la URL al cargar la página y prerellenan un campo de código de referido/inscripción usando JS vanilla al final de cada archivo.

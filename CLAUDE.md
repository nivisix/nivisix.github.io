# CLAUDE.md

Este archivo proporciona orientación a Claude Code (claude.ai/code) al trabajar con el código de este repositorio.

## Descripción General

Sitio estático en GitHub Pages para **Nívisix Soluciones**. Sin herramientas de compilación, gestor de paquetes ni transpilación — los archivos se sirven directamente tal como están.

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

Tres páginas, todas autocontenidas (sin plantillas compartidas ni generador estático):

| Archivo | Propósito |
|---------|-----------|
| `index.html` | Página principal corporativa — navegación, servicios, formulario de contacto, Google Maps |
| `finanzas-en-accion.html` | Landing page del curso de educación financiera — video YouTube, visor PDF, formulario de registro |
| `finanzas-hari-om.html` | Versión co-branded del curso con "Hari Om Espacio" |

Cada página importa su propio CSS/JS al final y usa la grilla de Bootstrap 3. Las secciones son bloques `<div id="...">` con anclas; la barra de navegación fija usa scroll suave.

### Organización de Assets
- `assets/css/` — `style.css` hoja principal, `media-queries.css` breakpoints, `buttons.css` / `form-elements.css` sobrescrituras específicas
- `assets/js/scripts.js` — JS personalizado: scroll-spy, menú móvil, Select2, Masonry, Google Maps, animaciones de labels, lectura del parámetro `?ref=` para códigos de referido
- `assets/bootstrap/` — Bootstrap 3 (CSS + JS + Glyphicons); no actualizar sin probar todas las páginas
- `assets/js/` — jQuery 1.10.2 más plugins (Masonry, Select2, Magnific Popup, Backstretch, EmailJS)
- `assets/fonts/` — Tipografía Signika (formatos webfont)
- `assets/img/` — Organizado en `icons/`, `portfolio/`, `team/`, `slider/`; variantes retina usan el sufijo `@2x`

### Integraciones de Terceros
- **EmailJS** — Formularios de contacto a `nivisix.soluciones@gmail.com` vía servicio `service_gc4pvxe` / plantilla `template_yzr484j` (claves públicas del cliente, no secretos)
- **Google Analytics** — ID de seguimiento `G-3ZWR725QH8`
- **Google Maps API** — Cargado por HTTP; coordenadas en `scripts.js` hardcodeadas (apuntan a Nueva York, no a la ubicación del negocio)

### Flujo de Inscripción a Cursos
`finanzas-en-accion.html` y `finanzas-hari-om.html` leen el parámetro `ref` de la URL al cargar y prerellenan el campo de código de referido con JS vanilla al final de cada archivo.

## Paleta de Colores

- Verde azulado principal: `#0098A7` / `#3497A8`
- Azul marino: `#2B6CA7`
- Aguamarina claro: `#9ccbc0`
- Fondo oscuro: `#464c5c`

## Despliegue

Push a `main` — GitHub Pages despliega automáticamente. Sin configuración de CI/CD.

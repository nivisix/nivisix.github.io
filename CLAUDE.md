# CLAUDE.md

Este archivo proporciona orientación a Claude Code (claude.ai/code) al trabajar con el código de este repositorio.

## Descripción del proyecto

Sitio estático en GitHub Pages para **Nívisix Soluciones**, empresa de soluciones tecnológicas con sede en México. No hay herramientas de compilación, gestor de paquetes ni transpilación — se editan los archivos y se hace push directamente.

## Desarrollo

Abrir cualquier archivo HTML en un navegador para previsualizar localmente. Para servir con recarga en vivo, cualquier servidor de archivos estáticos funciona (ej. `python -m http.server 8080`). No hay pruebas, linting ni pasos de compilación.

## Arquitectura

Tres páginas, todas autocontenidas (sin plantillas compartidas ni generador estático):

| Archivo | Propósito |
|---------|-----------|
| `index.html` | Página principal corporativa — navegación, servicios, formulario de contacto, Google Maps |
| `finanzas-en-accion.html` | Página del curso de educación financiera — video de YouTube, visor de PDF, formulario de registro |
| `finanzas-hari-om.html` | Versión co-branded del curso con "Hari Om Espacio" |

Todas las páginas comparten:
- Bootstrap 3 (en `assets/bootstrap/`)
- jQuery 1.10.2 (`assets/js/jquery-1.10.2.min.js`)
- Fuentes Signika personalizadas (`assets/fonts/`)
- ID de Google Analytics: `G-3ZWR725QH8`
- EmailJS para formularios de contacto (servicio: `service_gc4pvxe`, plantilla: `template_yzr484j`)

La lógica JS personalizada está en `assets/js/scripts.js`: desplazamiento suave, menú móvil, portafolio masonry/filtro/lightbox y lectura del parámetro `?code=` de la URL para códigos de referido.

## Servicios externos clave

- **EmailJS** — envía envíos de formularios a `nivisix.soluciones@gmail.com`
- **Google Analytics** — propiedad GA4 cargada vía gtag
- **YouTube** — videos embebidos en las páginas de cursos
- **PDFs** — `finanzas.pdf` y `FINANZAS-HARIOM.pdf` servidos desde la raíz del repositorio

## Paleta de colores

- Verde azulado principal: `#0098A7` / `#3497A8`
- Azul marino: `#2B6CA7`
- Aguamarina claro: `#9ccbc0`
- Fondo oscuro: `#464c5c`

## Despliegue

Push a `main` — GitHub Pages despliega automáticamente. Sin configuración de CI/CD.

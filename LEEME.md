# TERSHOP ONLINE — Catálogo interactivo

Este proyecto contiene una primera versión de la galería de catálogos para publicar en GitHub Pages.

## Archivos
- `index.html`: aplicación completa.
- `assets/logo-tershop.webp`: logotipo proporcionado.
- `assets/fondo-tela-negra.webp`: fondo proporcionado.

## Importante sobre Google Drive
El listado original contiene 17 enlaces a carpetas. Una página HTML estática no puede enumerar por sí sola los archivos dentro de carpetas de Drive. Para mostrar automáticamente miniaturas, nombres y descargas individuales, esta versión usa Google Drive API v3.

Las carpetas deben permitir lectura a cualquier persona que tenga el enlace. Esto no cambia permisos ni evita restricciones de Drive. Si una carpeta no es accesible como lectora, el catálogo mostrará un error y seguirá ofreciendo el botón para abrir la carpeta original.

## Configurar Google Drive API (una sola vez)
1. Entra en Google Cloud Console: https://console.cloud.google.com/
2. Crea un proyecto o selecciona uno.
3. En APIs y servicios > Biblioteca, habilita **Google Drive API**.
4. En APIs y servicios > Credenciales, crea una **Clave de API**.
5. Restringe la clave:
   - Restricción de aplicación: sitios web (referentes HTTP).
   - Añade tu dominio de GitHub Pages, por ejemplo `https://TUUSUARIO.github.io/*`.
   - Restricción de API: solo Google Drive API.
6. Antes de publicar, abre `index.html` en un editor y busca `const DRIVE_API_KEY`. Sustituye `PEGA_AQUI_TU_CLAVE_API_RESTRINGIDA` por tu clave API restringida. Así la galería podrá cargar para todos los visitantes. La sección **Configuración de conexión (administrador)** sirve para pruebas locales en tu propio navegador; una clave guardada allí no se comparte con los clientes.

**Nota:** la clave API será visible para los visitantes porque la aplicación es estática. Por eso es imprescindible restringirla por referente HTTP y por API. No uses una clave sin restricciones.

## Publicar en GitHub Pages
1. Crea un repositorio público llamado `tershop-catalogos`.
2. Sube `index.html` y la carpeta `assets` manteniendo esa estructura.
3. En Settings > Pages, selecciona Deploy from a branch, rama `main` y carpeta `/ (root)`.
4. Guarda y espera a que GitHub Pages publique el sitio.
5. Comparte el enlace que GitHub te entregue.

## Próximo ajuste
Esta es una base funcional de interfaz y conexión. Antes de anunciarla a clientes, hay que probar la API con al menos una carpeta real y confirmar que Drive devuelve miniaturas y permite descargas. Si las descargas están bloqueadas por permisos, no se pueden habilitar desde el HTML.

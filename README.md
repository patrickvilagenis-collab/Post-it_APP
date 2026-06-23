# Post-it_APP

Aplicación Kanban con Post-its: un tablero infinito donde crear notas adhesivas,
arrastrarlas, cambiarles el color, editarlas y archivarlas cuando se completan.

## Uso

Abre `index.html` en el navegador. El estado se guarda automáticamente en
`localStorage` (modo local) y, opcionalmente, se sincroniza en la nube entre
todos tus dispositivos si configuras Supabase (ver más abajo).

### Funciones

- **Crear notas**: doble clic en el tablero o escribe en la barra superior y pulsa Enter.
- **Mover**: arrastra una nota. Arrastra el fondo para desplazarte por el tablero.
- **Editar**: clic sobre una nota.
- **Color**: pasa el ratón sobre la nota y elige un color para agrupar ideas.
- **Completar / eliminar**: usa ✓ para archivar y ✕ para borrar.
- **Tareas cerradas**: botón "Cerradas" para ver, restaurar o eliminar las archivadas.
- **Zoom y desplazamiento**: controles en la esquina inferior izquierda, rueda del ratón o pellizco en trackpad.

## Sincronización entre dispositivos (Supabase)

Por defecto la app guarda solo en el navegador (`localStorage`), que es por
dispositivo y no se comparte. Para ver y editar las mismas notas en el móvil y
el ordenador en tiempo real, conéctala a Supabase (gratis):

1. Sigue la guía paso a paso en [`SUPABASE_SETUP.md`](./SUPABASE_SETUP.md).
2. Rellena tus credenciales en [`config.js`](./config.js).
3. Pulsa **Compartir** en la cabecera para copiar el enlace del tablero (`#board=...`)
   y ábrelo en tus otros dispositivos.

El indicador de la cabecera muestra **☁ Sincronizado** o **● Local** según el estado.
Si no configuras Supabase, todo sigue funcionando en modo local.

## Online (GitHub Pages)

El proyecto es un sitio estático (`index.html` + `config.js`), listo para publicarse
con GitHub Pages. Para activarlo: **Settings → Pages → Build and deployment →
Source: Deploy from a branch**, y selecciona la rama y la carpeta raíz (`/`).

# Post-it_APP

Aplicación Kanban con Post-its: un tablero infinito donde crear notas adhesivas,
arrastrarlas, cambiarles el color, editarlas y archivarlas cuando se completan.

## Uso

Abre `index.html` en el navegador. No requiere servidor ni dependencias: todo
funciona en local y el estado se guarda automáticamente en `localStorage`.

### Funciones

- **Crear notas**: doble clic en el tablero o escribe en la barra superior y pulsa Enter.
- **Mover**: arrastra una nota. Arrastra el fondo para desplazarte por el tablero.
- **Editar**: clic sobre una nota.
- **Color**: pasa el ratón sobre la nota y elige un color para agrupar ideas.
- **Completar / eliminar**: usa ✓ para archivar y ✕ para borrar.
- **Tareas cerradas**: botón "Cerradas" para ver, restaurar o eliminar las archivadas.
- **Zoom y desplazamiento**: controles en la esquina inferior izquierda, rueda del ratón o pellizco en trackpad.

## Online (GitHub Pages)

El proyecto es un único `index.html` estático, listo para publicarse con GitHub Pages.
Para activarlo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
y selecciona la rama y la carpeta raíz (`/`).

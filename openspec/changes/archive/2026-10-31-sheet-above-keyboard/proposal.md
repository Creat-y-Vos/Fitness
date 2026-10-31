## Why
En Android (Chrome/PWA) el teclado se dibuja encima de la página sin achicarla. Las hojas modales están ancladas abajo, así que el teclado tapa el botón principal (Guardar, Registrar peso) y el usuario tiene que cerrar el teclado para tocarlo. Pasa en todas las hojas con campos de texto.

## What Changes
- Las hojas se levantan por encima del teclado y limitan su alto al espacio visible.
- Al enfocar un campo dentro de una hoja, el campo y el botón de acción quedan a la vista.
- El viewport declara `interactive-widget=resizes-content` para que Chrome Android achique el área en lugar de superponer el teclado.

## Capabilities
### Modified Capabilities
- `workout-sessions`: requisito sobre hojas de edición y teclado.

## Impact
- `index.html` (meta viewport, CSS de `.modal-root .sheet`, módulo `Keyboard`), `sw.js` y `APP_VERSION` (v35).

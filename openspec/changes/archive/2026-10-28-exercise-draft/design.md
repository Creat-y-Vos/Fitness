# Design

## Decisions

- **Almacenamiento**: `localStorage` bajo una clave propia (`vform.drafts`), con la forma `{ "YYYY-MM-DD|ejercicio": { sets, obs, grip, ts } }`. Fuera de `Store` para no sincronizarlo ni mezclarlo con los datos reales.
- **Cuándo se guarda**: al cambiar un campo, tocar en la hoja o escribir en observaciones, con un pequeño retardo. Los pasos de los selectores numéricos disparan `change` sin burbujeo, por eso el oyente va en fase de captura.
- **Guardas**: el oyente ignora hojas que no sean la de ese ejercicio y deja de guardar tras guardar o quitar, para que un guardado pendiente no reviva el borrador.
- **Prioridad**: si hay borrador, se muestra el borrador en lugar de lo guardado; el aviso lo explica y permite descartarlo.
- **Limpieza**: se borran los borradores de otros días al leer o guardar.

## Risks / Trade-offs

- Un borrador viejo del mismo día puede sorprender. Mitigación: aviso visible y botón para descartar.
- Si se cambia de celular a mitad de entreno, el borrador no viaja. Es aceptable.

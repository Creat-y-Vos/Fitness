## Why

Si Fabi carga series en un ejercicio y sale de la hoja sin tocar "Guardar", pierde lo que puso. En medio del entrenamiento es fácil salir sin querer (o para mirar otra cosa) y volver a cargar todo.

## What Changes

- Lo que se carga en la hoja de un ejercicio (series, observaciones y agarre) se guarda solo como borrador en el dispositivo, aunque no se toque "Guardar".
- Al volver a abrir ese ejercicio el mismo día, se recupera el borrador, con un aviso y la opción de descartarlo.
- Guardar o quitar el ejercicio borra el borrador. Los borradores de días anteriores se eliminan.
- Un borrador no cuenta para el progreso, los récords ni el historial: eso solo ocurre al guardar.

## Impact

- `index.html`: `Sheets.exercise` y un auxiliar de borradores.
- Spec afectada: `workout-sessions` (requisito nuevo).
- Los borradores viven solo en el dispositivo; no se sincronizan con la nube.

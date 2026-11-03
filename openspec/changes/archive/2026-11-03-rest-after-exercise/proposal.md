## Why
El cronómetro de descanso arranca al sumar una serie, pero no después de la última serie de un ejercicio: al guardar, el usuario pasa al siguiente ejercicio sin descanso guiado. El músculo necesita la misma recuperación tras la última serie que tras cualquiera de las otras.

## What Changes
- Al guardar un ejercicio, si la sesión no terminó, arranca el cronómetro de descanso con la duración por defecto de ese ejercicio.
- Si el ejercicio guardado era el último de la sesión, no arranca (sigue el cierre de sesión).

## Capabilities
### Modified Capabilities
- `workout-sessions`: descanso después de guardar un ejercicio.

## Impact
- `index.html` (guardado de ejercicio), `sw.js`, `APP_VERSION` v41.

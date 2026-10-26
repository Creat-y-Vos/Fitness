## Why

El lunes 26/10, con Torso A en el plan, Fabi cargó la dominada y la pantalla pasó a "Full body + V". La app deduce la sesión por los ejercicios ya cargados; la dominada está en todas las sesiones, hay empate y gana la primera de la lista, no la que toca por el plan.

## What Changes

- Al deducir la sesión por lo registrado, en caso de empate gana la sesión que corresponde al día según el plan.
- Si lo registrado coincide más con otra sesión, se mantiene la deducción actual.
- La elección manual de sesión no cambia.

## Impact

- `index.html`: `Plan.inferSession`.
- Spec afectada: `workout-sessions` (requisito nuevo).
- Sin cambios de datos ni de base.

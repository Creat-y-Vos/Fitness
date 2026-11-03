## Why
La rutina de elongación real de Fabi (15 estiramientos, 26 bloques con lados) difiere de la rutina por defecto. Además, con su molestia lumbar, en algunas poses (flexiones adelante, flexor de cadera de pie) conviene recordar la técnica mientras corre el cronómetro.

## What Changes
- La rutina de Fabi se carga en `user_config.daily[elongacion].routine` (nombre, lados y una indicación opcional por pose).
- El cronómetro muestra la indicación de la pose bajo el nombre.
- Los lados se muestran como "lado izquierdo / lado derecho".
- Sin cambios para quien no declara indicaciones.

## Capabilities
### Modified Capabilities
- `daily-checks-and-activities`: la elongación guiada admite indicaciones por pose.

## Impact
- `index.html` (`Stretch.blocks`, hoja del cronómetro), `sw.js`, `APP_VERSION` v38; `user_config.daily` de Fabi.

## Why
En las fases 2 y 3 el plan de Fabi tenía piernas el jueves, reemplazando la caminata/trote de martes y jueves que es su hábito, y nadie se lo avisó. Además, el viernes (Torso V) quedaba como día de V sin piernas pero el jueves de piernas dejaba la prensa a 72 h del fútbol sin necesidad. Se revisó contra el objetivo (V, cintura, fútbol del domingo, molestia lumbar) y se decidió otra estructura.

## What Changes
- Fases 2 y 3: lunes Torso A, miércoles Torso B, viernes Torso V; martes y jueves cardio (caminata/trote 45 min).
- Piernas y core en dosis cortas: curl femoral + plancha al final de Torso A, prensa moderada al final de Torso B, plancha en Torso V.
- Nueva regla de planificación: las piernas se reparten en dosis cortas, lejos del fútbol del domingo; nunca pesadas el viernes ni el sábado.
- Los datos viven en `user_config` (no hay cambio de código en la app).

## Capabilities
### Modified Capabilities
- `workout-sessions`: agrega el requisito de ubicación de piernas respecto al fútbol.

## Impact
- Datos: `user_config` de Fabi (phases 2/3, sessions torsoA/torsoB/torsoV, coachContext).
- Sin cambios en `index.html` ni `sw.js`.

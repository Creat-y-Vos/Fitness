## Why
Los estiramientos no necesitan la misma duración. Los flexores de cadera, isquios y pecho (los que más se acortan por estar sentado y los que cargan la lumbar) rinden más con más tiempo; los de soltar (cuello, antebrazo, tríceps) cumplen con poco. Hoy todo dura 12 s.

## What Changes
- Cada pose de la rutina puede declarar `hold` (segundos). Sin `hold` se usan 12 s.
- Rutina de Fabi: 30 s flexores de cadera, isquios (hacia cada pierna y torso a 90°) y pecho; 20 s gemelos y cuádriceps; 12 s el resto.
- El botón de Home ya no promete "12 s + 3 s".

## Capabilities
### Modified Capabilities
- `daily-checks-and-activities`: la duración de la pose es configurable por pose.

## Impact
- `index.html` (`Stretch.blocks`, fase de pose), `sw.js`, `APP_VERSION` v39; `user_config.daily` de Fabi (`hold` y `meta`).

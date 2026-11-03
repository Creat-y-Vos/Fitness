## Why
La rutina completa de elongación dura unos 11 minutos. Después del gimnasio tiene sentido, pero en días sin gimnasio es mucho y se cae la constancia. Además la rutina carece de dorsales y glúteo, y repite flexiones adelante de isquios.

## What Changes
- Dos modos del cronómetro: **completa** y **corta**. La corta recorre solo las poses marcadas `short` en la rutina.
- Home muestra los dos botones; el aviso posterior al entreno abre la completa.
- Rutina de Fabi: se reemplaza "Flexión adelante, tocar los pies" por dorsales (30 s) y se suma glúteo por lado (30 s). La corta queda con flexor de cadera (rodilla en el piso), isquios a 90° y pecho.

## Capabilities
### Modified Capabilities
- `daily-checks-and-activities`: versión corta de la elongación guiada.

## Impact
- `index.html` (`Stretch.blocks/open`, botones de Home), `sw.js`, `APP_VERSION` v40; `user_config.daily` de Fabi.

## Why
La elongación son 10 estiramientos de 12 s cada uno. Hoy el usuario cuenta de cabeza o mira el reloj entre pose y pose, con el celular en una mano y los auriculares puestos.

## What Changes
- Cronómetro guiado de elongación: 12 s de pose y 3 s de cambio, con nombre de la pose, lado, pose siguiente y avance.
- Avisos con sonido corto y vibración al empezar cada pose y en los últimos 3 s del cambio.
- Pausa, saltar pose y cerrar. La pantalla queda encendida mientras corre.
- Al terminar toda la rutina se tilda "Elongación" del día.
- Se abre desde Home y desde el aviso posterior al entreno.
- La rutina vive en `user_config.daily` (campo `routine`), con valores por defecto en la app.

## Capabilities
### Modified Capabilities
- `daily-checks-and-activities`: requisito de elongación guiada.

## Impact
- `index.html` (módulo `Stretch`, botones en Home y en `postWorkout`), `sw.js`, `APP_VERSION` v37; `user_config.daily` de Fabi.

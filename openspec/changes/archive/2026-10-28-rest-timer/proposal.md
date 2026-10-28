## Why

Durante el entreno Fabi controla el descanso entre series con el reloj del celular, fuera de la app. El descanso es una de las variables que más afecta el rendimiento y hoy la app no ayuda con eso.

## What Changes

- Un temporizador de descanso flotante, visible en toda la app mientras corre.
- Arranca solo al tocar "＋ Serie" en la hoja del ejercicio, y también a mano con un botón "Descanso".
- Duración por defecto según el ejercicio, ajustable con +15 s y −15 s.
- Al terminar vibra y suena un beep corto, ambos desactivables en Ajustes.

## Impact

- `index.html`: hoja del ejercicio (`Sheets.exercise`), un componente flotante nuevo y Ajustes.
- Spec afectada: `workout-sessions` (requisito nuevo).
- Sin cambios de datos ni de base.
- Fuera de alcance: avisos con la pantalla bloqueada (requieren notificaciones push), guardar el historial de descansos, mantener la pantalla encendida.

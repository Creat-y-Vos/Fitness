## Why

En el primer uso real del temporizador (28/10) no vibró y Fabi quiere además un pitido audible si tiene auriculares puestos. La causa más probable es que la pantalla se apagó durante el descanso (el descanso dura más que el tiempo de bloqueo del celular) y una web app no puede avisar con la pantalla apagada; en auriculares inalámbricos un pitido corto además se pierde porque el audio tarda en despertar.

## What Changes

- Mientras corre el descanso, la app mantiene la pantalla encendida (cuando el dispositivo lo permite).
- La vibración al terminar es más larga y marcada.
- El aviso sonoro pasa a tres pitidos precedidos de un tono suave, para que se oigan también por auriculares inalámbricos.
- Se vuelve a pedir el bloqueo de pantalla si la app vuelve a primer plano con el descanso corriendo.

## Impact

- `index.html`: módulo `Rest`.
- Spec afectada: `workout-sessions` (requisito "Temporizador de descanso").
- Se saca de "fuera de alcance" el mantener la pantalla encendida. Sigue fuera de alcance avisar con la pantalla bloqueada a mano (requiere notificaciones push).
- Límite: la vibración no existe en iPhone y no se puede verificar el audio por auriculares desde el entorno de pruebas; se confirma en el celular.

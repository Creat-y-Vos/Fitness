# Design

## Decisions

- **Wake Lock de pantalla** (`navigator.wakeLock.request("screen")`) al iniciar el descanso; se libera al terminar o cerrar. El navegador lo suelta al pasar a segundo plano, así que se vuelve a pedir en `visibilitychange` si el descanso sigue corriendo. Si la API no existe, la app sigue como antes.
- **Vibración**: patrón largo `[400, 150, 400, 150, 400]`.
- **Sonido**: un tono suave de 440 Hz (lead-in) y luego tres pitidos de 880 Hz cada 0,5 s. El lead-in despierta el enlace de auriculares Bluetooth, que suelen recortar el comienzo del audio. El contexto de audio se reanuda al avisar.
- Se mantienen los ajustes de vibración y sonido y la regla de no avisar si se vuelve muy tarde.

## Risks / Trade-offs

- La pantalla encendida gasta batería, pero solo mientras corre un descanso (1 a 2 minutos).
- Si el celular se bloquea a mano, no hay aviso: es una limitación de las web apps.

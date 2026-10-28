## Why

Si Fabi entrena escuchando música o un podcast, el pitido del descanso se pierde debajo. Quiere que, mientras suenan los pitidos, el resto del audio del celular baje de volumen para oírlos.

## What Changes

- El aviso sonoro se reproduce como un sonido corto de tipo "transitorio", el que el sistema operativo suele tratar bajando el volumen del resto del audio mientras dura (o mezclándolo), en lugar de un oscilador de Web Audio, que se mezcla sin avisar.
- Cuando está disponible, se declara además el tipo de sesión de audio como transitorio durante el aviso.
- Si el navegador rechaza la reproducción, se usa el pitido de Web Audio de antes.

## Impact

- `index.html`: módulo `Rest` (aviso sonoro).
- Spec afectada: `workout-sessions` (requisito nuevo).
- Límite importante: una web app no puede forzar que otra aplicación baje el volumen. Que lo haga depende del sistema operativo, del navegador y de la app de música. Esto es el mejor esfuerzo posible y se confirma en el celular; si no alcanza, la alternativa es una aplicación nativa.

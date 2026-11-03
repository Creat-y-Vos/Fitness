## Why
Las máquinas con pila de placas en libras (por ejemplo la de bíceps) ofrecen cargas como 9, 14, 18, 23, 27, 32, 36 kg. El botón "+" de la app suma un salto fijo (`step`), así que desde 0 o desde cualquier valor nunca cae en esas cargas y hay que tipearlas a mano.

## What Changes
- Un ejercicio puede declarar `stack`: la lista ordenada de cargas reales de la máquina.
- Con `stack`, "+" y "−" saltan a la carga siguiente o anterior de la lista.
- La carga sugerida se redondea a la carga más cercana de la lista.
- Se carga `stack` del bíceps en máquina (pila de 10 en 10 lb) en el config del usuario.

## Capabilities
### Modified Capabilities
- `workout-sessions`: requisito de cargas de pila.

## Impact
- `index.html` (`UI.stepper`, `Plan.suggestKg`), `sw.js`, `APP_VERSION` v36; `user_config.exercises` de Fabi.

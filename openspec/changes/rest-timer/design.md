# Design

## Context

La hoja del ejercicio se cierra al guardar y se reabre por ejercicio, así que un contador dentro de la hoja se pierde. Un contador a nivel de app, flotante, sobrevive a cualquier navegación.

## Decisions

- **Componente flotante único** sobre la barra inferior, con tiempo restante, +15 s, −15 s y cerrar. Un solo temporizador a la vez: iniciar otro reemplaza al anterior.
- **Disparador**: tocar "＋ Serie" arranca el descanso; además hay un botón manual "Descanso" en la hoja.
- **Cuenta por hora de fin** (`Date.now()` contra un instante de fin), no por segundos acumulados: si la app pasa a segundo plano o el celular se bloquea, al volver muestra el valor correcto.
- **Duraciones por defecto**: ejercicios de fuerza pesados y dominadas 120 s; accesorios 75 s; core y ejercicios por tiempo 45 s. Un ejercicio puede traer `rest` (segundos) en la configuración y eso manda. Son valores de partida, no una prescripción del plan.
- **Aviso al terminar**: `navigator.vibrate` y un beep corto con Web Audio, iniciado tras un toque del usuario. Ambos se pueden apagar en Ajustes y se guardan en el dispositivo.

## Risks / Trade-offs

- Con la pantalla bloqueada no hay aviso confiable en una web app; la vibración no existe en iPhone. Mitigación: al volver, el contador muestra "listo". Una solución completa pide notificaciones push (fuera de alcance).
- Tocar "＋ Serie" arranca el descanso aunque no se haya terminado la serie. Mitigación: se cierra con ✕ y es un toque.

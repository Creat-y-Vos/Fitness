# Proposal

## Why

Las dominadas con agarre prono, neutro y supino no exigen lo mismo (el supino y el neutro permiten más repeticiones). Hoy la app no registra el agarre, así que una serie con neutro se cuenta como récord de dominada estricta y el coach semanal puede leerla como una mejora de fuerza que no ocurrió. Fabi ya probó agarre neutro esta semana.

## What Changes

- Al registrar `dominada` o `dominada-asist`, el usuario elige el agarre: prono (por defecto), neutro o supino.
- Solo las series con agarre prono cuentan para la mejor serie estricta, el récord y la meta de dominadas.
- Las series con otros agarres se registran y se muestran por separado, sin tocar el récord.
- Las sesiones anteriores sin agarre se interpretan como prono.
- La vista `workout_sets` expone el agarre para que el coach semanal compare prono contra prono.
- El coach semanal menciona las series con otros agarres aparte, sin contarlas como progreso.

## Capabilities

### New Capabilities

### Modified Capabilities
- `pullup-tracking`: la serie estricta pasa a depender del agarre; se agrega el registro del agarre.
- `weekly-coach-note`: la nota compara dominadas solo entre series del mismo agarre.

## Impact

- `index.html`: hoja de registro del ejercicio, cálculo de dominada estricta e historial.
- Supabase: la vista `workout_sets` (columna nueva `grip`). No cambian tablas ni RLS.
- Tarea semanal del coach: leer `grip` y comparar por agarre.
- Fuera de alcance: ancho de agarre (normal o ancho), agarre en otros ejercicios (jalón, remo), y reescribir el historial automáticamente.

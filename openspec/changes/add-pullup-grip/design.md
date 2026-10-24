# Design

## Context

Cada ejercicio de una sesión se guarda como `{ sets: [{kg, v}], obs }` dentro de `workouts.exercises` (jsonb). La vista `workout_sets` expande las series con `jsonb_each` y `jsonb_array_elements`, y hoy expone kg, value y obs. La dominada estricta se calcula en el cliente a partir de `dominada` y `dominada-asist` con kg igual a 0. Ver proposal.md para el motivo.

## Goals / Non-Goals

**Goals:**
- Que el récord y la meta solo se muevan con series en prono.
- No romper sesiones ya guardadas ni la sincronización.

**Non-Goals:**
- Ancho de agarre, y agarre en jalón o remo.
- Reescribir el historial sin que el usuario lo indique.

## Decisions

- **El agarre se guarda por ejercicio dentro de la sesión (`grip`), no por serie.** Fabi hace una variante por ejercicio y sesión; por serie complicaría la hoja sin aportar. Alternativa descartada: campo en cada serie.
- **Valores `prono`, `neutro`, `supino`; ausencia = prono.** Evita migrar datos y mantiene compatibles los registros previos.
- **Solo el prono alimenta `bestReps`, el récord y el `pullupTarget`.** Los otros agarres se calculan aparte con la misma lógica.
- **La vista `workout_sets` suma `e.val ->> 'grip'`** (con prono por defecto). Es un `CREATE OR REPLACE VIEW` que agrega una columna al final, sin romper consultas existentes. Ojo: `CREATE OR REPLACE VIEW` pierde `security_invoker=true`; hay que volver a aplicarlo con `ALTER VIEW ... SET (security_invoker = true)` (ya hecho y verificado).
- **Sin cambios en tablas ni RLS.** El campo vive dentro del jsonb existente.
- Dibujos del agarre: SVG en línea dentro del index.html (sin imágenes externas, funcionan offline). Vista frontal de la barra con las manos: prono = palmas hacia afuera, neutro = palmas enfrentadas, supino = palmas hacia uno. Trazo con `currentColor` para tema claro/oscuro. Cada opción lleva dibujo y nombre.

## Risks / Trade-offs

- Registros viejos hechos en neutro quedan como prono hasta que el usuario los corrija; mitigación: editar esas sesiones a mano (se pregunta cuáles en la tarea 4).
- Dos dispositivos con versiones distintas: el viejo ignora `grip` y lo puede perder al guardar el mismo ejercicio. Mitigación: tarea de versión y caché, y avisar que se abra la app dos veces.
- Más campos en la hoja del ejercicio: el selector va solo en dominadas para no ensuciar los demás.

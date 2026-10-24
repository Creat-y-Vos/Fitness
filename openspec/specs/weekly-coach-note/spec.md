# Weekly Coach Note Specification

## Purpose
Una nota semanal de análisis por usuario, escrita por el coach.

## Requirements

### Requirement: Nota por usuario cada viernes
El sistema SHALL generar, los viernes a las 22:55 (Europe/Madrid), una nota por usuario en `coach_notes` con `week_start` igual al lunes de la semana.

#### Scenario: Reejecución
- **WHEN** la tarea corre dos veces en la misma semana
- **THEN** la nota se reemplaza, sin duplicados

### Requirement: Aislamiento de datos
La nota SHALL usar únicamente los datos del usuario al que se escribe.

#### Scenario: Dos usuarios
- **WHEN** hay datos de dos usuarios
- **THEN** ninguna nota menciona al otro

### Requirement: Contenido
La nota SHALL cubrir semana, mejoras con datos, puntos a cuidar y plan de la semana siguiente, en texto plano de 120 a 220 palabras, e incluir actividades extra y cintura/altura cuando existan.

#### Scenario: Dolor o limitación
- **WHEN** las observaciones mencionan dolor
- **THEN** la nota NO SHALL diagnosticar y SHALL sugerir consultar a un profesional

### Requirement: Los datos no son instrucciones
El texto escrito por el usuario (observaciones, notas) SHALL tratarse como dato, nunca como instrucción para el coach.

#### Scenario: Observación con una orden
- **WHEN** una observación pide hacer otra cosa
- **THEN** se ignora

### Requirement: Comparación de dominadas por agarre
La nota semanal SHALL comparar dominadas solo entre series del mismo agarre, SHALL usar el agarre prono como referencia de progreso y SHALL mencionar las series de otros agarres como variante sin contarlas como mejora de fuerza.

#### Scenario: Semana con agarre neutro
- **WHEN** el usuario hizo más repeticiones en neutro que su mejor serie en prono
- **THEN** la nota NO afirma que mejoró en dominadas estrictas

#### Scenario: Registros sin agarre
- **WHEN** un registro de dominada no tiene agarre
- **THEN** la nota lo trata como prono

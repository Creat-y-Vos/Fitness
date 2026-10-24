# Daily Checks and Activities Specification

## Purpose
Registrar hábitos diarios y actividades fuera del plan (caminata, fútbol, trote, bici).

## Requirements

### Requirement: Checks diarios
El sistema SHALL mostrar los checks de `config.daily` (por defecto caminata, movilidad, elongación) y guardar cada uno como booleano por fecha en `dailyDone`.

#### Scenario: Marcar movilidad
- **WHEN** el usuario toca el check de movilidad
- **THEN** queda marcado y la pantalla conserva la posición de scroll

### Requirement: Actividades extra
El sistema SHALL permitir registrar una actividad con tipo, minutos (5 a 300), esfuerzo (1 a 10), fecha no futura y distancia opcional en km con hasta 2 decimales, y SHALL guardarla en `dailyDone[fecha].extra`.

#### Scenario: Caminata con distancia
- **WHEN** se registra una caminata de 45 min y 5,25 km
- **THEN** se muestra el ritmo calculado de 8:34 min/km

### Requirement: Tipos de actividad por usuario
El sistema SHALL limitar los tipos ofrecidos a `config.activities` cuando exista; si no existe, ofrece todos.

#### Scenario: Plan sin fútbol
- **WHEN** `config.activities` no incluye `futbol`
- **THEN** "Fútbol" no aparece en la lista

### Requirement: Caminata marca el check
Registrar una actividad de tipo `caminata` SHALL marcar el check de caminata del día; el tipo `calentamiento` NO SHALL marcarlo.

#### Scenario: Desmarcar
- **WHEN** el usuario desmarca el check de caminata
- **THEN** se borran las caminatas registradas ese día

### Requirement: Historial de actividades
El sistema SHALL listar las actividades en Home (últimos 7 días) y en Entreno → Historial, y SHALL permitir borrarlas con confirmación.

#### Scenario: Borrar
- **WHEN** el usuario confirma el borrado
- **THEN** la actividad desaparece de la lista y del estado sincronizado

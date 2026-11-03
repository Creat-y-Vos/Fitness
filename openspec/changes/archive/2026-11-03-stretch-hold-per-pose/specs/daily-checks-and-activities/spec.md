## ADDED Requirements

### Requirement: Duración de la pose configurable
Cada pose de la rutina de elongación SHALL poder declarar su propia duración en segundos, y el cronómetro SHALL usarla para esa pose; las poses sin duración declarada SHALL durar 12 segundos.

#### Scenario: Pose con duración propia
- **WHEN** la pose "Pecho" declara 30 segundos
- **THEN** la pose dura 30 segundos y el cambio a la siguiente dura 3 segundos

#### Scenario: Pose sin duración
- **WHEN** la pose no declara duración
- **THEN** dura 12 segundos

## ADDED Requirements

### Requirement: Indicaciones por pose en la elongación guiada
Cuando una pose de la rutina de elongación declara una indicación, el cronómetro SHALL mostrarla bajo el nombre de la pose mientras dura la preparación y la pose.

#### Scenario: Pose con indicación
- **WHEN** la pose "Flexor de cadera de pie" declara una indicación
- **THEN** la indicación se ve bajo el nombre en la preparación y en la pose

#### Scenario: Pose sin indicación
- **WHEN** la pose no declara indicación
- **THEN** no se muestra línea de indicación

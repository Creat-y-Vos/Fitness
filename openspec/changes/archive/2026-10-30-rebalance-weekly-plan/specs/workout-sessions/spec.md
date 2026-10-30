## ADDED Requirements

### Requirement: Piernas lejos del fútbol del domingo
El plan SHALL repartir el trabajo de piernas en dosis cortas dentro de las sesiones de fuerza de lunes y miércoles, y SHALL NOT programar piernas pesadas el viernes ni el sábado cuando el usuario juega al fútbol el domingo.

#### Scenario: Semana con fútbol el domingo
- **WHEN** la fase tiene sesiones de fuerza lunes, miércoles y viernes
- **THEN** la prensa está en la sesión del miércoles y la sesión del viernes no incluye ejercicios de piernas de carga

#### Scenario: Día de cardio
- **WHEN** el día es martes o jueves de las fases 2 y 3
- **THEN** Home muestra caminata o trote y no una sesión de gimnasio

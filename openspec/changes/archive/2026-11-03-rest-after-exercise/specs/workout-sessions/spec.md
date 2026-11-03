## ADDED Requirements

### Requirement: Descanso después de guardar un ejercicio
Al guardar un ejercicio, si todavía quedan ejercicios de la sesión sin registrar, el sistema SHALL iniciar el cronómetro de descanso con la duración por defecto del ejercicio guardado, y SHALL NOT iniciarlo si el ejercicio guardado completó la sesión.

#### Scenario: Ejercicio intermedio
- **WHEN** el usuario guarda un ejercicio y aún quedan ejercicios por registrar
- **THEN** el cronómetro de descanso arranca con la duración por defecto de ese ejercicio

#### Scenario: Último ejercicio
- **WHEN** el usuario guarda el último ejercicio de la sesión
- **THEN** no arranca el cronómetro y se ofrece el cierre de sesión

## ADDED Requirements

### Requirement: La sesión del día no cambia por ejercicios compartidos
Cuando el sistema deduce la sesión de un día a partir de los ejercicios ya registrados y varias sesiones coinciden por igual, SHALL elegir la sesión que corresponde a ese día según el plan de la fase.

#### Scenario: Primer ejercicio compartido
- **WHEN** el plan del día es Torso A y el único ejercicio registrado es `dominada`, que está en todas las sesiones
- **THEN** la sesión mostrada sigue siendo Torso A

#### Scenario: Otra sesión coincide más
- **WHEN** lo registrado coincide en más ejercicios con otra sesión que con la planificada
- **THEN** se muestra esa otra sesión

## ADDED Requirements

### Requirement: Cargas de pila de máquina
Cuando un ejercicio declara `stack` (lista ordenada de cargas reales de la máquina), los botones de sumar y restar carga SHALL moverse a la carga siguiente o anterior de la lista, y la carga sugerida SHALL redondearse a la carga más cercana de la lista.

#### Scenario: Sumar desde una carga de la lista
- **WHEN** el ejercicio tiene `stack` 9, 14, 18, 23 y la carga actual es 18
- **THEN** sumar lleva a 23 y restar lleva a 14

#### Scenario: Carga que no está en la lista
- **WHEN** el usuario tipeó 20 kg y el `stack` tiene 18 y 23
- **THEN** sumar lleva a 23 y restar lleva a 18

#### Scenario: Ejercicio sin lista
- **WHEN** el ejercicio no declara `stack`
- **THEN** los botones suman y restan el `step` del ejercicio

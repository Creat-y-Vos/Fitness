## ADDED Requirements

### Requirement: Elongación guiada con cronómetro
El sistema SHALL ofrecer un cronómetro de elongación que recorre la rutina del usuario con 12 segundos de pose y 3 segundos de cambio entre poses, SHALL mostrar la pose actual, su lado y la siguiente, SHALL avisar con sonido y vibración el comienzo de cada pose y los últimos segundos del cambio, y SHALL tildar la elongación del día al completar la rutina.

#### Scenario: Rutina completa
- **WHEN** el usuario inicia la elongación guiada y deja correr todos los bloques
- **THEN** cada pose dura 12 segundos, cada cambio dura 3 segundos y al terminar queda tildada "Elongación" de hoy

#### Scenario: Cierre a medias
- **WHEN** el usuario cierra la elongación guiada antes de terminar
- **THEN** la elongación del día no se tilda

#### Scenario: Pausa
- **WHEN** el usuario pausa y reanuda
- **THEN** el tiempo restante de la fase actual no cambia durante la pausa

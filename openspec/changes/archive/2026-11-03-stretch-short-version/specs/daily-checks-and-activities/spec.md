## ADDED Requirements

### Requirement: Versión corta de la elongación guiada
El sistema SHALL ofrecer una versión corta de la elongación guiada que recorre solo las poses marcadas como cortas en la rutina del usuario, y SHALL tildar la elongación del día al completarla igual que la versión completa.

#### Scenario: Elegir la corta
- **WHEN** el usuario inicia la versión corta
- **THEN** el cronómetro recorre solo las poses marcadas como cortas

#### Scenario: Sin poses marcadas
- **WHEN** la rutina no marca ninguna pose como corta
- **THEN** la versión corta recorre la rutina completa

## ADDED Requirements

### Requirement: Aviso sonoro sobre otro audio
El aviso sonoro del descanso SHALL reproducirse como un sonido corto de tipo transitorio, para que el sistema pueda bajar el volumen de otro audio que esté sonando mientras dura, y SHALL volver al pitido anterior si el navegador no permite esa reproducción.

#### Scenario: Aviso como sonido transitorio
- **WHEN** el descanso llega a cero con el sonido activado
- **THEN** el aviso se reproduce como un archivo de audio corto y, si la API existe, la sesión de audio se declara transitoria mientras suena

#### Scenario: Reproducción rechazada
- **WHEN** el navegador rechaza reproducir el archivo de audio
- **THEN** suena el pitido de respaldo

#### Scenario: Sonido desactivado
- **WHEN** el usuario desactivó el sonido en Ajustes
- **THEN** no se reproduce ningún audio

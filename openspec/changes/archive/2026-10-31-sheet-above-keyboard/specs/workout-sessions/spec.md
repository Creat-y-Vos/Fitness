## ADDED Requirements

### Requirement: El teclado no tapa las hojas
Cuando el teclado del dispositivo está abierto, las hojas modales SHALL quedar por encima de él, y el campo enfocado y el botón de acción de la hoja SHALL poder verse y tocarse sin cerrar el teclado.

#### Scenario: Registrar peso con teclado abierto
- **WHEN** el usuario abre "Registrar peso" y el teclado ocupa la parte baja de la pantalla
- **THEN** el botón de guardar queda visible sobre el teclado

#### Scenario: Hoja más alta que el espacio visible
- **WHEN** el contenido de la hoja no entra en el espacio sobre el teclado
- **THEN** la hoja limita su alto y el contenido se desplaza dentro de ella, con el campo enfocado a la vista

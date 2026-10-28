## ADDED Requirements

### Requirement: Borrador del ejercicio en edición
El sistema SHALL conservar en el dispositivo lo cargado en la hoja de un ejercicio (series, observaciones y agarre) aunque el usuario salga sin guardar, y SHALL recuperarlo al abrir ese ejercicio el mismo día. El borrador NO SHALL contar para el progreso, los récords ni el historial hasta que se guarde.

#### Scenario: Salir sin guardar
- **WHEN** el usuario carga series, cierra la hoja sin guardar y vuelve a abrir el ejercicio el mismo día
- **THEN** ve las mismas series y observaciones, con un aviso de que son un borrador sin guardar

#### Scenario: Guardar borra el borrador
- **WHEN** el usuario guarda el ejercicio
- **THEN** el borrador desaparece y al reabrir se ve lo guardado

#### Scenario: Descartar
- **WHEN** el usuario toca "Descartar borrador"
- **THEN** el borrador se borra y la hoja vuelve a lo guardado, o a una serie vacía si no hay nada guardado

#### Scenario: Otro día
- **WHEN** existe un borrador de un día anterior
- **THEN** no se usa y se elimina

#### Scenario: Sin efecto en el progreso
- **WHEN** hay un borrador sin guardar
- **THEN** no aparece en el historial ni cambia récords ni comparaciones

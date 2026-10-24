# Pull-up Tracking Specification

## Purpose
Seguir la evolución hacia la dominada estricta, si el plan del usuario tiene meta de dominadas.

## Requirements

### Requirement: Visible solo con meta de dominadas
El sistema SHALL mostrar dominadas (pestaña, tarjeta de Home, estadísticas, mensajes) únicamente cuando `goal.pullupTarget` es mayor a 0.

#### Scenario: Usuario sin meta de dominadas
- **WHEN** `pullupTarget` es 0
- **THEN** no aparece nada relacionado con dominadas

### Requirement: Dominada estricta
Una serie SHALL contar como estricta cuando su agarre es prono y es del ejercicio `dominada`, o del ejercicio `dominada-asist` con asistencia de 0 kg. Las series con agarre neutro o supino NO SHALL contar como estrictas, aunque no tengan asistencia.

#### Scenario: Asistida sin asistencia
- **WHEN** una serie de `dominada-asist` en prono tiene kg igual a 0
- **THEN** cuenta como dominada estricta

#### Scenario: Neutro sin asistencia
- **WHEN** una serie de `dominada` se registra con agarre neutro
- **THEN** NO cuenta como dominada estricta

### Requirement: Mejor serie
El sistema SHALL calcular la mejor serie estricta como el máximo de repeticiones en una sola serie estricta entre todas las sesiones, con un piso en `baseline.pullupReps`, y SHALL mostrar aparte la mejor serie de cada otro agarre.

#### Scenario: Nuevo récord
- **WHEN** el usuario guarda una serie estricta mayor al mejor anterior
- **THEN** se muestra un aviso de récord

#### Scenario: Más repeticiones en neutro
- **WHEN** el usuario guarda una serie neutra con más repeticiones que su mejor estricta
- **THEN** NO se muestra aviso de récord y la serie aparece como mejor de agarre neutro

### Requirement: Agarre de la dominada
Al registrar `dominada` o `dominada-asist`, el sistema SHALL permitir elegir el agarre entre prono, neutro y supino, SHALL proponer prono por defecto y SHALL guardar la elección junto con las series de ese ejercicio en esa sesión.

#### Scenario: Registrar con agarre neutro
- **WHEN** el usuario elige neutro y guarda sus series de dominada
- **THEN** la sesión guarda el agarre neutro para ese ejercicio

#### Scenario: Sin elegir
- **WHEN** el usuario guarda sin tocar el selector
- **THEN** el agarre queda como prono

### Requirement: Sesiones anteriores sin agarre
El sistema SHALL tratar como prono cualquier registro de dominada que no tenga agarre.

#### Scenario: Historial previo
- **WHEN** existe una sesión guardada antes de esta función
- **THEN** sus series cuentan como prono

### Requirement: Ilustración del agarre
El selector de agarre SHALL mostrar junto a cada opción un dibujo de la posición de las manos y su nombre, de modo que cualquier persona identifique el agarre sin conocer los términos. Los dibujos SHALL verse bien en tema claro y oscuro y SHALL ser parte de la app, sin depender de la red.

#### Scenario: Elegir mirando el dibujo
- **WHEN** el usuario abre la hoja de una dominada
- **THEN** ve las tres opciones con su dibujo y nombre, y la elegida queda resaltada

#### Scenario: Sin conexión
- **WHEN** el usuario abre el selector sin red
- **THEN** los dibujos se muestran igual

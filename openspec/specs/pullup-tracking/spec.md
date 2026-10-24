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
Una serie SHALL contar como estricta cuando es del ejercicio `dominada`, o del ejercicio `dominada-asist` con asistencia de 0 kg.

#### Scenario: Asistida sin asistencia
- **WHEN** una serie de `dominada-asist` tiene kg igual a 0
- **THEN** cuenta como dominada estricta

### Requirement: Mejor serie
El sistema SHALL calcular la mejor serie estricta como el máximo de repeticiones en una sola serie entre todas las sesiones, con un piso en `baseline.pullupReps`.

#### Scenario: Nuevo récord
- **WHEN** el usuario guarda una serie estricta mayor al mejor anterior
- **THEN** se muestra un aviso de récord

# Workout Sessions Specification

## Purpose
Registrar entrenos de gimnasio según un plan por fases, con cargas de referencia y progresión.

## Requirements

### Requirement: Plan por fases desde la fecha de inicio
El sistema SHALL calcular la fase actual (1 reentrada, 2 reconstrucción, 3 progresión) a partir de `profile.returnDate` y SHALL mostrar la regla de la fase en Home.

#### Scenario: Fase 1 las primeras dos semanas
- **WHEN** hay menos de 14 días desde `returnDate`
- **THEN** la sesión usa el factor de carga y el tope de series de la fase 1

#### Scenario: Sin fecha de inicio
- **WHEN** `returnDate` está vacío
- **THEN** el sistema SHALL mostrar un botón para empezar y no asumir fase

### Requirement: Sesión según el día de la semana
El sistema SHALL elegir la sesión del día con el mapa `days` de la fase y SHALL permitir elegir otra sesión manualmente para hoy.

#### Scenario: Día de entrenamiento
- **WHEN** el día de la semana tiene sesión en la fase actual
- **THEN** Home muestra la sesión y el botón "Empezar sesión"

### Requirement: Registro de series
El sistema SHALL guardar por ejercicio una lista de series con repeticiones (`v`) y, si el ejercicio es de carga, kilos (`kg`), más una observación opcional.

#### Scenario: Guardar un ejercicio
- **WHEN** el usuario guarda al menos una serie con valor mayor a 0
- **THEN** el ejercicio queda en el entreno de hoy y se compara contra la sesión anterior

### Requirement: Carga sugerida
El sistema SHALL sugerir el peso como `ref × factor de fase`, redondeado al salto del ejercicio, salvo en ejercicios marcados `noScale`.

#### Scenario: Ejercicio sin referencia
- **WHEN** el ejercicio no tiene `ref`
- **THEN** no se muestra carga sugerida

### Requirement: Cierre de sesión
Al guardar el último ejercicio de la sesión, el sistema SHALL ofrecer marcar movilidad y elongación pendientes del día.

#### Scenario: Ya estaban marcadas
- **WHEN** movilidad y elongación ya están marcadas hoy
- **THEN** no se muestra el aviso

### Requirement: Hojas de edición
Las hojas modales SHALL poder cerrarse deslizando hacia abajo, siguiendo el dedo, cuando su contenido está arriba de todo.

#### Scenario: Arrastre corto
- **WHEN** el usuario suelta antes de unos 110 px
- **THEN** la hoja vuelve a su lugar

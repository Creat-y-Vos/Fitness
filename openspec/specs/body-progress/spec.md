# Body Progress Specification

## Purpose
Seguir peso, medidas, fotos e indicadores corporales hacia el objetivo.

## Requirements

### Requirement: Peso y objetivo
El sistema SHALL registrar pesos por fecha y mostrar peso actual, meta y kilos acumulados.

#### Scenario: Peso nuevo
- **WHEN** el usuario registra un peso
- **THEN** el gráfico y la tendencia semanal se actualizan

### Requirement: Medidas
El sistema SHALL registrar las medidas definidas en `config.measures` y mostrar su evolución.

#### Scenario: Cintura
- **WHEN** hay al menos una medida de cintura
- **THEN** se puede ver su gráfico

### Requirement: IMC
El sistema SHALL calcular el IMC con la altura del perfil y mostrar un velocímetro con las zonas de la OMS, la marca de la meta, la tabla de categorías con kilos equivalentes y la relación cintura/altura cuando exista cintura.

#### Scenario: Sin altura
- **WHEN** `profile.heightCm` no está cargado
- **THEN** se muestra un botón para cargarla en Ajustes

### Requirement: Perfil corporal
El sistema SHALL permitir cargar altura (100 a 230 cm), sexo y año de nacimiento, todos opcionales.

#### Scenario: Valor inválido
- **WHEN** la altura está fuera de rango
- **THEN** no se guarda

### Requirement: Fotos de progreso
El sistema SHALL permitir subir fotos por pose y fecha asignada por el usuario, compararlas ordenadas por esa fecha y capturarlas con una guía y la cámara frontal.

#### Scenario: Comparador
- **WHEN** hay al menos dos fotos de una pose
- **THEN** se compara la más reciente contra la anterior por fecha asignada

# Per-user Config Specification

## Purpose
Que cada cuenta vea su propio plan, objetivo y textos, sin datos de otro usuario.

## Requirements

### Requirement: Config del servidor manda
El sistema SHALL leer `user_config.config` de la cuenta y usarla sobre los valores por defecto; lo que falte SHALL salir de los defaults.

#### Scenario: Cuenta sin config
- **WHEN** no existe fila en `user_config`
- **THEN** se usan los defaults del código

### Requirement: Solo lectura desde la app
La app NO SHALL escribir `user_config`; el plan lo escribe el coach.

#### Scenario: Ajustes
- **WHEN** el usuario cambia ajustes
- **THEN** se guardan en su perfil, no en `user_config`

### Requirement: Textos según el objetivo
Los mensajes del coach, las estadísticas y las actividades SHALL adaptarse a la config (dominadas, tipos de actividad) y NO SHALL mostrar contenido de otro objetivo.

#### Scenario: Cuenta sin dominadas
- **WHEN** `pullupTarget` es 0
- **THEN** no aparecen frases sobre espalda ni dominadas

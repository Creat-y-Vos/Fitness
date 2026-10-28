## ADDED Requirements

### Requirement: Temporizador de descanso
El sistema SHALL mostrar un temporizador de descanso flotante, visible en toda la app mientras corre, SHALL iniciarlo al agregar una serie con "＋ Serie" y mediante un botón "Descanso", y SHALL permitir sumar o restar 15 segundos y cerrarlo. Al llegar a cero SHALL avisar con vibración y un sonido corto, salvo que el usuario los haya desactivado en Ajustes.

#### Scenario: Arranque al agregar una serie
- **WHEN** el usuario toca "＋ Serie" en la hoja de un ejercicio
- **THEN** empieza una cuenta regresiva con la duración por defecto de ese ejercicio y se ve el temporizador flotante

#### Scenario: Duración por ejercicio
- **WHEN** el ejercicio trae una duración de descanso en la configuración
- **THEN** el temporizador usa esa duración en lugar de la de por defecto

#### Scenario: Cierra la hoja
- **WHEN** el usuario cierra la hoja del ejercicio con el temporizador corriendo
- **THEN** el temporizador sigue visible y corriendo

#### Scenario: App en segundo plano
- **WHEN** el usuario vuelve a la app después de haberla dejado en segundo plano
- **THEN** el temporizador muestra el tiempo restante real, o "listo" si ya terminó

#### Scenario: Sin avisos
- **WHEN** el usuario desactivó vibración y sonido
- **THEN** al llegar a cero el temporizador no vibra ni suena y solo muestra "listo"

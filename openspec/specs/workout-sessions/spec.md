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

### Requirement: La sesión del día no cambia por ejercicios compartidos
Cuando el sistema deduce la sesión de un día a partir de los ejercicios ya registrados y varias sesiones coinciden por igual, SHALL elegir la sesión que corresponde a ese día según el plan de la fase.

#### Scenario: Primer ejercicio compartido
- **WHEN** el plan del día es Torso A y el único ejercicio registrado es `dominada`, que está en todas las sesiones
- **THEN** la sesión mostrada sigue siendo Torso A

#### Scenario: Otra sesión coincide más
- **WHEN** lo registrado coincide en más ejercicios con otra sesión que con la planificada
- **THEN** se muestra esa otra sesión

### Requirement: Temporizador de descanso
El sistema SHALL mostrar un temporizador de descanso flotante, visible en toda la app mientras corre, SHALL iniciarlo al agregar una serie con "＋ Serie" y mediante un botón "Descanso", y SHALL permitir sumar o restar 15 segundos y cerrarlo. Mientras corre SHALL mantener la pantalla encendida cuando el dispositivo lo permita. Al llegar a cero SHALL avisar con una vibración marcada y tres pitidos audibles también por auriculares conectados, salvo que el usuario los haya desactivado en Ajustes.

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

#### Scenario: Pantalla encendida durante el descanso
- **WHEN** corre un descanso
- **THEN** la pantalla se mantiene encendida hasta que termina o se cierra, y se libera después

#### Scenario: Aviso al terminar
- **WHEN** el descanso llega a cero con los avisos activos
- **THEN** el dispositivo vibra con un patrón largo y suenan tres pitidos precedidos de un tono suave

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

### Requirement: Piernas lejos del fútbol del domingo
El plan SHALL repartir el trabajo de piernas en dosis cortas dentro de las sesiones de fuerza de lunes y miércoles, y SHALL NOT programar piernas pesadas el viernes ni el sábado cuando el usuario juega al fútbol el domingo.

#### Scenario: Semana con fútbol el domingo
- **WHEN** la fase tiene sesiones de fuerza lunes, miércoles y viernes
- **THEN** la prensa está en la sesión del miércoles y la sesión del viernes no incluye ejercicios de piernas de carga

#### Scenario: Día de cardio
- **WHEN** el día es martes o jueves de las fases 2 y 3
- **THEN** Home muestra caminata o trote y no una sesión de gimnasio

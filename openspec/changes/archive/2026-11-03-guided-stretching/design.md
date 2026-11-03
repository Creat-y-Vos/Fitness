## Decisiones
- **Tiempos por marcas de reloj (`endAt`)**, no por cuenta de ticks: sobrevive a pestañas en segundo plano y a pausas.
- **Rutina de 18 bloques**: los estiramientos de un solo lado se hacen por lado (izquierda y derecha) y los simétricos (aductores, pecho) una vez. 18 × 12 s + 17 × 3 s ≈ 4 min 27 s.
- **Pitido corto por WebAudio**, no el de 3 pitidos del descanso (dura 1,8 s y el cambio dura 3 s). Un tono al empezar la pose, tres tonos cortos en los últimos 3 s del cambio.
- **Tilda sola al completar** la rutina; si se cierra a medias no tilda.
- **Rutina editable** desde `user_config.daily[elongacion].routine` (`[{n, sides}]`); sin ese campo se usa la rutina por defecto de la app.

## Riesgos
- Sin audio con pantalla bloqueada (límite de la web): por eso se mantiene la pantalla encendida.
- Si hacer cada lado en 12 s es demasiado largo o corto, se ajusta en la configuración.

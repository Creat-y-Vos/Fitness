# Design

## Context

Web Audio (`AudioContext`) se mezcla con el resto del audio sin pedirle foco al sistema, por eso la música no baja. Los elementos `<audio>` sí participan del foco de audio del navegador, y los sonidos cortos pueden pedir foco transitorio. Además existe la API experimental `navigator.audioSession`, con el tipo `"transient"` para sonidos breves.

## Decisions

- **El aviso se genera como un archivo WAV en memoria** (tono previo suave y tres pitidos, unos 1,8 s, mismo patrón que antes) y se reproduce con un elemento `<audio>`.
- **`navigator.audioSession.type = "transient"`** mientras suena, si la API existe, y se restablece a `"auto"` al terminar.
- **Respaldo**: si `play()` falla (política de reproducción automática), se usa el pitido de Web Audio.
- No se reproduce nada para "desbloquear" el audio en cada descanso: eso haría que la música se pause o baje al tocar "＋ Serie". Se apoya en que la página ya tuvo interacción del usuario.

## Risks / Trade-offs

- Según el sistema y la app de música, puede bajar el volumen, pausarla un instante o no hacer nada. No se puede verificar desde el entorno de pruebas.
- Dos caminos de sonido (archivo y Web Audio) a mantener.

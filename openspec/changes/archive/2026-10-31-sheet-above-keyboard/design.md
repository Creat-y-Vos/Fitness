## Decisiones
- **Dos capas.** `interactive-widget=resizes-content` resuelve Chrome Android moderno; `visualViewport` calcula `--kb` como respaldo (iOS Safari y navegadores que superponen el teclado).
- **`--kb` = innerHeight − visualViewport.height − offsetTop**, mínimo 0. La hoja usa `bottom: var(--kb)` y `max-height: min(88dvh, 100dvh − kb − 12px)`; el contenido scrollea dentro.
- **Foco**: en `focusin` de input/select/textarea dentro de la hoja, `scrollIntoView({block:"center"})` tras ~250 ms, cuando el teclado ya terminó de abrir.
- No se toca el arrastre para cerrar ni las animaciones.

## Riesgos
- Si ambas capas actúan a la vez, `--kb` vale 0 (la ventana ya se achicó), así que no se duplica el desplazamiento.
- No se puede probar con un teclado real en el sandbox; se simula con `visualViewport` falso y se confirma en el teléfono.

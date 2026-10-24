# Design

## Context

El service worker ya hacía `skipWaiting` y `clients.claim`, pero la página abierta seguía ejecutando el código viejo hasta el próximo arranque. Además `fetch` de la navegación podía devolver una copia de `index.html` guardada por el navegador (GitHub Pages sirve con caché de unos 10 minutos).

## Decisions

- **Recarga al cambiar el controlador (`controllerchange`)**, solo si la página ya tenía uno al cargar: en la primera instalación no se recarga.
- **Cuándo se busca una versión**: al cargar, al volver a primer plano (`visibilitychange`) y cada 30 minutos, con `reg.update()`.
- **Registro con `updateViaCache: "none"`** y navegación con `cache: "no-cache"`; el precarga del shell pide cada archivo con `cache: "reload"`.
- **No interrumpir**: si hay una hoja abierta o un campo con foco, se reintenta cada 3 segundos.
- **No perder datos**: antes de recargar se intenta `Sync.push()` con un tope de 3 segundos; lo local ya está guardado en el dispositivo.
- Una sola recarga por versión (bandera), para evitar bucles.

## Risks / Trade-offs

- Una recarga inesperada mientras se mira la pantalla. Mitigación: solo ocurre fuera de hojas y de escritura, y no hay cartel ni espera.
- Si un dispositivo no tiene red al volver, sigue con la versión que tiene hasta tenerla.

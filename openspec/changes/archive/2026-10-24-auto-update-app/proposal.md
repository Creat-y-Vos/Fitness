## Why

Hoy una versión nueva exige que el usuario cierre y abra la app dos veces. Fabi lo sufre en cada publicación (se quedó en v24 con la v25 ya publicada) y en la app de su esposa pasa lo mismo. La actualización no debería depender de que la persona sepa hacer eso.

## What Changes

- La app detecta sola una versión nueva (al abrir, al volver a primer plano y cada 30 minutos) y se recarga sin intervención.
- No interrumpe: si hay una hoja abierta o la persona está escribiendo, espera a que termine.
- Antes de recargar sube lo pendiente a la nube, para no perder datos.
- La página y el service worker se piden sin usar la copia vieja del navegador (el motivo por el que a veces se veía la versión anterior).
- Cambia el requisito "Versión y caché": ya no hay que abrir dos veces.

## Impact

- `sw.js` y el registro del service worker en `index.html`.
- Spec afectada: `accounts-and-sync` (requisito "Versión y caché").
- Límite: los celulares que hoy corren una versión anterior a esta necesitan la doble apertura una última vez; desde ahí es automático.
- Fuera de alcance: avisar con un cartel "hay versión nueva" (la recarga es silenciosa); actualizaciones con la app cerrada del todo.

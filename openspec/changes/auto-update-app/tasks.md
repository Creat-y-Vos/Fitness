# Tasks

## 1. Service worker

- [x] 1.1 Precargar el shell con `cache: "reload"` y pedir la navegación con `cache: "no-cache"`

## 2. Página

- [x] 2.1 Registrar con `updateViaCache: "none"` y buscar versión al cargar, al volver a primer plano y cada 30 minutos
- [x] 2.2 Recargar al cambiar el controlador, solo si ya había uno, sin interrumpir hojas ni campos, y subiendo lo pendiente antes

## 3. Verificación y publicación

- [x] 3.1 Probar en el navegador: nueva versión del service worker provoca una recarga; con hoja abierta espera; la primera instalación no recarga
- [ ] 3.2 Subir `APP_VERSION` y el caché, publicar y archivar

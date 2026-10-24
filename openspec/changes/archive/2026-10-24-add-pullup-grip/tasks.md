# Tasks

## 1. Datos

- [x] 1.1 Actualizar la vista `workout_sets` para exponer `grip` (prono si falta), con `CREATE OR REPLACE VIEW`
- [x] 1.2 Verificar que las consultas existentes del coach siguen funcionando

## 2. Registro en la app

- [x] 2.1 Agregar el selector de agarre (prono, neutro, supino) a la hoja de `dominada` y `dominada-asist`, con prono por defecto
- [x] 2.2 Dibujar tres íconos SVG en línea (prono, neutro, supino) en el estilo de la app, legibles en tema claro y oscuro, y usarlos en el selector
- [x] 2.3 Guardar `grip` junto a `sets` y `obs` y cargarlo al reabrir el ejercicio

## 3. Cálculo y vistas

- [x] 3.1 Hacer que la dominada estricta, la mejor serie, el récord y la meta cuenten solo agarre prono
- [x] 3.2 Mostrar por separado la mejor serie de neutro y supino en la vista de dominadas
- [x] 3.3 Mostrar el agarre en el historial de sesiones

## 4. Coach semanal

- [x] 4.1 Actualizar el prompt de la tarea semanal para comparar por agarre (prono como referencia)
- [x] 4.2 Preguntar a Fabi qué sesiones de esta semana fueron neutro y marcarlas

## 5. Verificación y publicación

- [x] 5.1 Probar en el navegador: guardar en cada agarre, reabrir, récord solo en prono
- [x] 5.2 Probar que una sesión sin `grip` se lee como prono
- [x] 5.3 Subir `APP_VERSION` y el caché del service worker, publicar y archivar el cambio

# Accounts and Sync Specification

## Purpose
Cuentas por usuario con sincronización entre dispositivos y datos aislados por RLS.

## Requirements

### Requirement: Acceso con email y contraseña
El sistema SHALL requerir inicio de sesión y SHALL ofrecer recuperación de contraseña por email.

#### Scenario: Olvidé mi contraseña
- **WHEN** el usuario pide recuperar su acceso
- **THEN** recibe un enlace que lo vuelve a la app para elegir una contraseña nueva

### Requirement: Aislamiento por usuario
Cada cuenta SHALL leer y escribir solo sus filas, protegido por RLS.

#### Scenario: Otro usuario
- **WHEN** una cuenta consulta datos de otra
- **THEN** no obtiene filas

### Requirement: Sincronización
El estado SHALL guardarse en el dispositivo y sincronizarse con el servidor; entrenos y medidas SHALL persistir en tablas propias.

#### Scenario: Segundo dispositivo
- **WHEN** el usuario entra desde otro dispositivo
- **THEN** ve sus mismos datos

### Requirement: Versión y caché
Cada publicación SHALL subir `APP_VERSION` y el nombre del caché del service worker. La app SHALL detectar una versión nueva al abrirse, al volver a primer plano y periódicamente, y SHALL recargarse sola con ella, sin que el usuario cierre y abra la app, esperando a que no haya una hoja abierta ni un campo en edición y subiendo antes lo pendiente a la nube.

#### Scenario: Publicación
- **WHEN** se publica una versión nueva
- **THEN** la app la muestra sola, sin que el usuario tenga que abrirla dos veces

#### Scenario: Recarga automática
- **WHEN** la app detecta una versión nueva y no hay hoja abierta ni campo en edición
- **THEN** se recarga sola con la versión nueva

#### Scenario: Usuario en medio de una carga
- **WHEN** la app detecta una versión nueva mientras hay una hoja abierta
- **THEN** espera a que se cierre y recién entonces se recarga

# Módulo 6: Servicios Transversales del Sistema

Este módulo agrupa las entidades responsables de proporcionar funcionalidades de soporte al sistema, tales como la gestión segura de sesiones de usuario y el registro de auditoría de las operaciones realizadas. Estas tablas no forman parte del dominio de negocio de la farmacovigilancia, pero son fundamentales para garantizar la seguridad, trazabilidad y confiabilidad de la aplicación.

---

# Tabla: `refresh_token`

Almacena los tokens de actualización utilizados para renovar sesiones autenticadas sin requerir un nuevo inicio de sesión.

| Campo        | Tipo de Dato     | Nulo | Llave | Descripción / Regla de Negocio                             |
| :----------- | :--------------- | :--: | :---: | :--------------------------------------------------------- |
| `id`         | UNIQUEIDENTIFIER |  NO  |   PK  | Identificador único del token.                             |
| `token`      | VARCHAR(500)     |  NO  |  UNI  | Valor único del token de actualización.                    |
| `expires_at` | DATETIME         |  NO  |   -   | Fecha y hora de expiración del token.                      |
| `revoked`    | BOOLEAN          |  NO  |   -   | Indica si el token fue invalidado antes de su vencimiento. |
| `user_id`    | UNIQUEIDENTIFIER |  NO  |   FK  | Referencia al usuario propietario del token.               |

### Reglas de negocio

* Cada token pertenece a un único usuario.
* Un usuario puede tener múltiples tokens activos o históricos.
* Un token revocado no puede utilizarse para renovar una sesión.
* Una vez alcanzada la fecha de expiración, el token pierde automáticamente su validez.

---

# Tabla: `audit_log`

Registra todas las operaciones relevantes realizadas sobre el sistema para garantizar la auditoría y la trazabilidad de las acciones ejecutadas.

| Campo            | Tipo de Dato     | Nulo | Llave | Descripción / Regla de Negocio                      |
| :--------------- | :--------------- | :--: | :---: | :-------------------------------------------------- |
| `id`             | UNIQUEIDENTIFIER |  NO  |   PK  | Identificador único del registro de auditoría.      |
| `user_id`     | UNIQUEIDENTIFIER |  SÍ  |   FK  | Usuario autenticado asociado al registro de auditoría. Un mismo usuario puede generar múltiples registros. |
| `reporter_id` | UNIQUEIDENTIFIER |  SÍ  |   FK  | Reportante asociado al registro de auditoría. Un mismo reportante puede generar múltiples registros. |
| `action`         | VARCHAR(50)      |  NO  |   -   | Operación realizada (Create, Update, Delete, View). |
| `entity_name`    | VARCHAR(150)     |  NO  |   -   | Nombre de la entidad afectada.                      |
| `entity_id`      | UNIQUEIDENTIFIER |  SÍ  |   -   | Identificador del registro afectado.                |
| `details`        | TEXT             |  SÍ  |   -   | Descripción legible de la operación.                |
| `old_values`     | TEXT             |  SÍ  |   -   | Estado anterior del registro en formato JSON.       |
| `new_values`     | TEXT             |  SÍ  |   -   | Estado posterior del registro en formato JSON.      |
| `ip_address`     | VARCHAR(50)      |  SÍ  |   -   | Dirección IP desde donde se ejecutó la acción.      |
| `created_at`     | DATETIME         |  NO  |   -   | Fecha y hora del evento registrado.                 |

### Reglas de negocio

* El sistema registra automáticamente las operaciones críticas.
* El registro puede asociarse a un usuario autenticado o a un reportante anónimo.
* Los campos `old_values` y `new_values` permiten reconstruir los cambios realizados sobre una entidad.
* Los registros de auditoría son inmutables y no deben modificarse una vez creados.
* La información almacenada permite realizar tareas de monitoreo, trazabilidad y análisis forense.

---

## Resumen de relaciones

```text
USUARIO (1) -------- (N) REFRESH_TOKEN

USUARIO (1) -------- (N) AUDIT_LOG
                 (opcional)

REPORTANTE_ANONIMO
        |
        +---------- AUDIT_LOG
           (1,N)
```

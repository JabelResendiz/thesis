# Módulo 5: Asignación y Evaluación

Este módulo gestiona el proceso de atención y evaluación clínica de los reportes.

---

# Tabla: `alerta`

| Campo            | Tipo de Dato | Nulo |  Llave  | Descripción / Regla de Negocio  |
| :--------------- | :----------- | :--: | :-----: | :------------------------------ |
| `id_alerta`      | INT (11)     |  NO  |    PK   | Identificador único.            |
| `id_reporte`     | INT (11)     |  NO  | FK, UNI | Referencia a `reporte`.         |
| `id_jefe`        | INT (11)     |  NO  |    FK   | Jefe de vacunación notificado.  |
| `fecha_creacion` | DATETIME     |  NO  |    -    | Fecha de creación de la alerta. |
| `estado_alerta`  | ENUM         |  NO  |    -    | Activa o inhabilitada.          |

---

# Tabla: `asignacion`

| Campo               | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio               |
| :------------------ | :----------- | :--: | :---: | :------------------------------------------- |
| `id_asignacion`     | INT (11)     |  NO  |   PK  | Identificador único.                         |
| `id_alerta`         | INT (11)     |  NO  |   FK  | Referencia a `alerta`.                       |
| `id_medico`         | INT (11)     |  NO  |   FK  | Médico evaluador asignado.                   |
| `fecha_asignacion`  | DATETIME     |  NO  |   -   | Fecha de asignación.                         |
| `estado_asignacion` | ENUM         |  NO  |   -   | Pendiente, completado, expirado o cancelado. |
| `fecha_fin`         | DATETIME     |  NO  |   -   | Fecha límite o fecha de finalización.        |

---

# Tabla: `evaluacion`

| Campo                   | Tipo de Dato | Nulo |  Llave  | Descripción / Regla de Negocio    |
| :---------------------- | :----------- | :--: | :-----: | :-------------------------------- |
| `id_evaluacion`         | INT (11)     |  NO  |    PK   | Identificador único.              |
| `id_asignacion`         | INT (11)     |  NO  | FK, UNI | Referencia a `asignacion`.        |
| `causalidad`            | ENUM         |  NO  |    -    | Clasificación de causalidad.      |
| `significancia_clinica` | ENUM         |  NO  |    -    | Impacto clínico del evento.       |
| `observaciones`         | TEXT         |  SÍ  |    -    | Comentarios del médico evaluador. |

---

## Resumen de relaciones

```text
REPORTE (1) ---- (1) ALERTA

JEFE_VACUNACION_MUNICIPAL (1) ---- (N) ALERTA

ALERTA (1) ---- (N) ASIGNACION

MEDICO_EVALUADOR (1) ---- (N) ASIGNACION

ASIGNACION (1) ---- (1) EVALUACION
```

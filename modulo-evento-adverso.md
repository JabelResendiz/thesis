# Módulo 4: Evento Adverso

Este módulo almacena las manifestaciones clínicas reportadas.

---

# Tabla: `sintoma`

| Campo         | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :------------ | :----------- | :--: | :---: | :----------------------------- |
| `id_sintoma`  | INT (11)     |  NO  |   PK  | Identificador único.           |
| `nombre`      | VARCHAR(150) |  NO  |   -   | Nombre del síntoma.            |
| `categoria`   | VARCHAR(100) |  NO  |   -   | Sistema orgánico asociado.     |
| `descripcion` | TEXT         |  SÍ  |   -   | Información complementaria.    |

---

# Tabla: `evento_adverso`

| Campo               | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :------------------ | :----------- | :--: | :---: | :----------------------------- |
| `id_evento_adverso` | INT (11)     |  NO  |   PK  | Identificador único.           |
| `id_reporte`        | INT (11)     |  NO  |   FK  | Referencia a `reporte`.        |
| `id_sintoma`        | INT (11)     |  NO  |   FK  | Referencia a `sintoma`.        |
| `fecha_inicio`      | DATE         |  NO  |   -   | Inicio del evento adverso.     |
| `fecha_fin`         | DATE         |  SÍ  |   -   | Fin del evento adverso.        |
| `intensidad`        | ENUM         |  NO  |   -   | Leve, moderado o severo.       |
| `gravedad`          | ENUM         |  NO  |   -   | Serio o no serio.              |
| `desenlace`         | ENUM         |  NO  |   -   | Estado final del evento.       |
| `descripcion`       | TEXT         |  SÍ  |   -   | Observaciones adicionales.     |

---

## Resumen de relaciones

```text
SINTOMA (1) ---- (N) EVENTO_ADVERSO

REPORTE (1) ---- (N) EVENTO_ADVERSO
```

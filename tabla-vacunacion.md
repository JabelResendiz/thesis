# Módulo 3: Vacunación

Este módulo almacena la información relacionada con las vacunas administradas.

---

# Tabla: `promotor`

| Campo         | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :------------ | :----------- | :--: | :---: | :----------------------------- |
| `id_promotor` | INT (11)     |  NO  |   PK  | Identificador único.           |
| `nombre`      | VARCHAR(150) |  NO  |   -   | Nombre del fabricante.         |
| `pais`        | VARCHAR(100) |  NO  |   -   | País de origen.                |

---

# Tabla: `vacuna`

| Campo                | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :------------------- | :----------- | :--: | :---: | :----------------------------- |
| `id_vacuna`          | INT (11)     |  NO  |   PK  | Identificador único.           |
| `id_promotor`        | INT (11)     |  NO  |   FK  | Referencia a `promotor`.       |
| `nombre`             | VARCHAR(150) |  NO  |   -   | Nombre de la vacuna.           |
| `tipo`               | ENUM         |  NO  |   -   | Plataforma tecnológica.        |
| `descripcion`        | TEXT         |  SÍ  |   -   | Información complementaria.    |
| `patologia_objetivo` | VARCHAR(150) |  NO  |   -   | Enfermedad que previene.       |

---

# Tabla: `lote`

| Campo         | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio  |
| :------------ | :----------- | :--: | :---: | :------------------------------ |
| `id_lote`     | INT (11)     |  NO  |   PK  | Identificador único.            |
| `id_vacuna`   | INT (11)     |  NO  |   FK  | Referencia a `vacuna`.          |
| `nombre_lote` | VARCHAR(100) |  NO  |   -   | Código del lote de fabricación. |

---

# Tabla: `centro_vacunacion`

| Campo          | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :------------- | :----------- | :--: | :---: | :----------------------------- |
| `id_centro`    | INT (11)     |  NO  |   PK  | Identificador único.           |
| `id_municipio` | INT (11)     |  NO  |   FK  | Municipio donde se encuentra.  |
| `nombre`       | VARCHAR(150) |  NO  |   -   | Nombre oficial del centro.     |
| `direccion`    | VARCHAR(250) |  NO  |   -   | Dirección física.              |

---

# Tabla: `vacunacion`

| Campo                  | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio    |
| :--------------------- | :----------- | :--: | :---: | :-------------------------------- |
| `id_vacunacion`        | INT (11)     |  NO  |   PK  | Identificador único.              |
| `id_reporte`           | INT (11)     |  NO  |   FK  | Referencia a `reporte`.           |
| `id_lote`              | INT (11)     |  NO  |   FK  | Referencia a `lote`.              |
| `id_centro`            | INT (11)     |  NO  |   FK  | Referencia a `centro_vacunacion`. |
| `sitio_administracion` | ENUM         |  NO  |   -   | Región anatómica de aplicación.   |
| `numero_dosis`         | ENUM         |  NO  |   -   | Dosis administrada.               |
| `fecha_administracion` | DATE         |  NO  |   -   | Fecha de vacunación.              |

---

## Resumen de relaciones

```text
PROMOTOR (1) ---- (N) VACUNA

VACUNA (1) ---- (N) LOTE

CENTRO_VACUNACION (1) ---- (N) VACUNACION

LOTE (1) ---- (N) VACUNACION

REPORTE (1) ---- (N) VACUNACION
```

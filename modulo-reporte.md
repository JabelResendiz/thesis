# Módulo 2: Gestión de Reportes

Este módulo almacena la información del sujeto vacunado, del reportante y del reporte ESAVI generado.

---

# Tabla: `persona`

Almacena los datos generales de las personas involucradas en el sistema.

| Campo              | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :----------------- | :----------- | :--: | :---: | :----------------------------- |
| `numero_identidad` | VARCHAR(11)  |  NO  |   PK  | Número de identidad oficial.   |
| `nombre`           | VARCHAR(150) |  NO  |   -   | Nombre completo de la persona. |
| `genero`           | ENUM         |  NO  |   -   | Género de la persona.          |
| `id_municipio`     | INT (11)     |  NO  |   FK  | Municipio de residencia.       |

---

# Tabla: `sujeto_vacunado`

Contiene la información específica del sujeto que recibió la vacuna.

| Campo              | Tipo de Dato | Nulo |  Llave | Descripción / Regla de Negocio                |
| :----------------- | :----------- | :--: | :----: | :-------------------------------------------- |
| `numero_identidad` | VARCHAR(11)  |  NO  | PK, FK | Referencia a la tabla `persona`.              |
| `embarazo`         | BOOLEAN      |  SÍ  |    -   | Indica si la persona se encuentra embarazada. |
| `contacto`         | VARCHAR(100) |  SÍ  |    -   | Teléfono o correo de contacto.                |
| `direccion`        | VARCHAR(250) |  SÍ  |    -   | Dirección del sujeto vacunado.                |
| `historia_medica`  | TEXT         |  SÍ  |    -   | Antecedentes médicos relevantes.              |

---

# Tabla: `reportante`

Contiene la información de la persona que realiza la notificación.

| Campo                | Tipo de Dato | Nulo |  Llave | Descripción / Regla de Negocio   |
| :------------------- | :----------- | :--: | :----: | :------------------------------- |
| `numero_identidad`   | VARCHAR(11)  |  NO  | PK, FK | Referencia a la tabla `persona`. |
| `relacion_sujeto`    | ENUM         |  NO  |    -   | Relación con el sujeto vacunado. |
| `correo_electronico` | VARCHAR(150) |  NO  |    -   | Medio principal de contacto.     |
| `numero_telefono`    | VARCHAR(30)  |  NO  |    -   | Medio alternativo de contacto.   |

---

# Tabla: `reporte`

Representa una notificación ESAVI registrada en el sistema.

| Campo            | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio       |
| :--------------- | :----------- | :--: | :---: | :----------------------------------- |
| `id_reporte`     | INT (11)     |  NO  |   PK  | Identificador único autoincremental. |
| `id_sujeto`      | VARCHAR(11)  |  NO  |   FK  | Referencia a `sujeto_vacunado`.      |
| `id_reportante`  | VARCHAR(11)  |  NO  |   FK  | Referencia a `reportante`.           |
| `fecha_creacion` | DATETIME     |  NO  |   -   | Fecha de creación del reporte.       |
| `estado_reporte` | ENUM         |  NO  |   -   | Estado actual del flujo de trabajo.  |
| `numero_recibo`  | VARCHAR(50)  |  NO  |  UNI  | Código único del reporte.            |

---

## Resumen de relaciones

```text
PERSONA (1) ---- (1) SUJETO_VACUNADO

PERSONA (1) ---- (1) REPORTANTE

SUJETO_VACUNADO (1) ---- (N) REPORTE

REPORTANTE (1) ---- (N) REPORTE
```

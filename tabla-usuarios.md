# Módulo 1: Gestión de Usuarios y Roles

Este módulo administra la autenticación, autorización y gestión de los perfiles internos del sistema.

---

# Tabla: `rol`

Almacena los perfiles funcionales disponibles dentro del sistema.

| Campo    | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio       |
| :------- | :----------- | :--: | :---: | :----------------------------------- |
| `id_rol` | INT (11)     |  NO  |   PK  | Identificador único autoincremental. |
| `nombre` | VARCHAR(100) |  NO  |  UNI  | Nombre del rol dentro del sistema.   |

---

# Tabla: `usuario`

Almacena las credenciales y datos generales de los usuarios del sistema.

| Campo                | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio                     |
| :------------------- | :----------- | :--: | :---: | :------------------------------------------------- |
| `id_usuario`         | INT (11)     |  NO  |   PK  | Identificador único autoincremental.               |
| `nombre`             | VARCHAR(150) |  NO  |   -   | Nombre completo del usuario.                       |
| `correo_electronico` | VARCHAR(150) |  NO  |  UNI  | Correo institucional utilizado para autenticación. |
| `password`           | VARCHAR(255) |  NO  |   -   | Contraseña almacenada mediante hash criptográfico. |
| `id_rol`             | INT (11)     |  NO  |   FK  | Referencia a la tabla `rol`.                       |

---

# Tabla: `jefe_vacunacion_municipal`

Representa a los jefes de vacunación registrados en el sistema.

| Campo              | Tipo de Dato | Nulo |  Llave | Descripción / Regla de Negocio            |
| :----------------- | :----------- | :--: | :----: | :---------------------------------------- |
| `id_usuario`       | INT (11)     |  NO  | PK, FK | Referencia a la tabla `usuario`.          |
| `id_municipio`     | INT (11)     |  NO  |   FK   | Municipio bajo su jurisdicción.           |
| `id_administrador` | INT (11)     |  NO  |   FK   | Administrador responsable de su registro. |

**Reglas de negocio**

* Existe una relación uno a uno con `usuario`.
* Un jefe solo puede gestionar reportes y médicos de su municipio.
* Todo jefe debe haber sido registrado por un administrador.

---

# Tabla: `medico_evaluador`

Representa a los médicos encargados de evaluar clínicamente los reportes ESAVI.

| Campo                         | Tipo de Dato | Nulo |  Llave | Descripción / Regla de Negocio                 |
| :---------------------------- | :----------- | :--: | :----: | :--------------------------------------------- |
| `id_usuario`                  | INT (11)     |  NO  | PK, FK | Referencia a la tabla `usuario`.               |
| `id_jefe`                     | INT (11)     |  NO  |   FK   | Jefe de vacunación responsable de su registro. |
| `institucion_atencion`        | VARCHAR(200) |  NO  |    -   | Institución donde ejerce sus funciones.        |
| `numero_registro_profesional` | VARCHAR(100) |  NO  |   UNI  | Número oficial otorgado por el MINSAP.         |
| `especialidad`                | VARCHAR(100) |  NO  |    -   | Especialidad médica del evaluador.             |

**Reglas de negocio**

* Existe una relación uno a uno con `usuario`.
* Un médico pertenece a un único jefe de vacunación.
* El número de registro profesional es único en todo el sistema.
* La especialidad proviene de un catálogo predefinido.

---

## Resumen de relaciones

```text
ROL (1) -------- (N) USUARIO

USUARIO (1) ---- (1) JEFE_VACUNACION_MUNICIPAL

USUARIO (1) ---- (1) MEDICO_EVALUADOR

JEFE_VACUNACION_MUNICIPAL (1) ---- (N) MEDICO_EVALUADOR
```

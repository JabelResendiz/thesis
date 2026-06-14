# Tabla: `usuarios`
Almacena las credenciales y datos de perfil de los usuarios del sistema web.

| Campo | Tipo de Dato | Nulo | Llave | Descripción / Regla de Negocio |
| :--- | :--- | :---: | :---: | :--- |
| `id` | INT (11) | NO | PAI | Identificador único autoincremental. |
| `email` | VARCHAR (150) | NO | UNI | Correo electrónico (sirve como login). |
| `password` | VARCHAR (255) | NO | - | Contraseña encriptada mediante bcrypt. |
| `role_id` | INT (11) | NO | FK | Vinculado a la tabla `roles`. |
| `created_at`| TIMESTAMP | SÍ | - | Fecha y hora de registro del usuario. |

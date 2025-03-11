Sistema de Autenticación con Spring Boot

Descripción del Proyecto

Este proyecto implementa un sistema de autenticación completo con Spring Boot, que incluye:

Login y Registro de usuarios.

Gestor de Roles y Permisos (Administrador y Usuario Estándar).

Seguridad mediante contraseñas encriptadas con BCrypt.

Manejo de Sesiones utilizando JWT.

Conexión a Base de Datos con Spring Data JPA y MySQL.

Funcionalidades Principales

Registro de nuevos usuarios.

Autenticación de usuarios existentes.

Control de acceso basado en roles (Administrador y Usuario Estándar).

Seguridad en la transmisión y almacenamiento de credenciales.

Opcional: Login con Google o Facebook usando OAuth 2.0.

Requisitos Previos

Java 21

Spring Boot 3.x

MySQL 8.x

Maven

Instalación y Configuración

Clonar el repositorio:

git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_PROYECTO>

Configurar la Base de Datos:

Asegúrate de tener una base de datos MySQL configurada. Modifica el archivo application.properties o application.yml con tus credenciales.

spring.datasource.url=jdbc:mysql://localhost:3306/autenticacion_db
spring.datasource.username=tu_usuario
spring.datasource.password=tu_contraseña
spring.jpa.hibernate.ddl-auto=update

Compilar el proyecto:

mvn clean install

Ejecutar la aplicación:

mvn spring-boot:run

Endpoints REST

Registro de Usuario

POST /api/auth/register

Request Body:

{
  "username": "usuario123",
  "email": "usuario@example.com",
  "password": "password123"
}

Login de Usuario

POST /api/auth/login

Request Body:

{
  "email": "usuario@example.com",
  "password": "password123"
}

Respuesta Exitosa:

{
  "token": "JWT-TOKEN"
}

Acceso a Recursos Protegidos

GET /api/admin/dashboard (Solo para Administradores)

GET /api/user/profile (Solo para Usuarios Autenticados)

Roles y Permisos

Rol

Permisos

Administrador

CRUD completo sobre usuarios y entidades.

Usuario

Acceso solo a sus propios datos (Read Only).

Seguridad

Contraseñas encriptadas con BCrypt.

Manejo de sesiones con JWT.

Autorización con anotaciones @PreAuthorize y @Secured.

Pruebas con Postman

Registrar un nuevo usuario.

Iniciar sesión para obtener un token JWT.

Usar el token en la cabecera Authorization: Bearer <JWT-TOKEN> para acceder a los endpoints protegidos.

Documentación Adicional

Documento FURPS+: Requisitos Funcionales, Usabilidad, Confiabilidad, Rendimiento y Soporte.

Guía Técnica: Descripción de la configuración de Spring Security y conexión a la base de datos.

Contribución

Realizar un fork del repositorio.

Crear una rama con la mejora o corrección: git checkout -b feature/nueva-funcionalidad

Hacer un pull request con los cambios.
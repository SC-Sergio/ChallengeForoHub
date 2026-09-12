# Challenge ForoHub

Backend REST educativo desarrollado con Java y Spring Boot para gestionar publicaciones de un foro. El proyecto forma parte del aprendizaje de backend con Alura Latam y está orientado a practicar una arquitectura por capas, persistencia con JPA, MySQL y migraciones con Flyway.

## Funcionalidad actual

La API expone actualmente dos operaciones sobre publicaciones (`Post`):

| Método | Endpoint | Descripción |
| --- | --- | --- |
| `GET` | `/api/posts` | Lista todas las publicaciones almacenadas |
| `POST` | `/api/posts` | Crea una nueva publicación |

El proyecto no implementa actualmente actualización, eliminación, autenticación ni autorización. Esta documentación describe únicamente las capacidades presentes en el código fuente.

## Arquitectura

La aplicación utiliza una estructura sencilla por capas:

```text
HTTP request
    |
    v
PostController
    |
    v
PostService
    |
    v
PostRepository (Spring Data JPA)
    |
    v
MySQL
```

### Capas principales

- **Controller:** recibe las solicitudes HTTP y expone los endpoints REST.
- **Service:** concentra la lógica de aplicación disponible para publicaciones.
- **Repository:** utiliza Spring Data JPA para persistencia.
- **Model:** define la entidad JPA `Post`.
- **Database migration:** Flyway crea la tabla `posts` mediante una migración versionada.

## Modelo `Post`

La entidad contiene actualmente:

- `id`
- `title`
- `content`
- `author`
- `createdAt`

`id` se genera automáticamente y `createdAt` se inicializa con la fecha/hora de creación.

## Stack

- Java 17
- Spring Boot 3.1.3
- Spring Web
- Spring Data JPA
- Spring Validation
- MySQL Connector/J 8.0.34
- Flyway
- Maven / Maven Wrapper
- JUnit 5 / Spring Boot Test

## Estructura del proyecto

```text
ChallengeForoHub/
|-- pom.xml
|-- mvnw
|-- mvnw.cmd
|-- src/
|   |-- main/
|   |   |-- java/ChallengeForoHub/
|   |   |   |-- controller/PostController.java
|   |   |   |-- model/Post.java
|   |   |   |-- repository/PostRepository.java
|   |   |   `-- service/PostService.java
|   |   `-- resources/
|   |       |-- application.properties
|   |       `-- db/migration/V1__Create_Table.sql
|   `-- test/
|       `-- java/ChallengeForoHub/ChallengeForoHubApplicationTests.java
`-- HELP.md
```

Los artefactos generados por Maven (`target/`) no forman parte del código fuente y están excluidos mediante `.gitignore`.

## Configuración de base de datos

La aplicación espera una base MySQL local llamada:

```text
foro_hub
```

Las credenciales no se guardan en el código fuente. Deben proporcionarse mediante variables de entorno:

```text
DB_USERNAME
DB_PASSWORD
```

Ejemplo en PowerShell:

```powershell
$env:DB_USERNAME="tu_usuario"
$env:DB_PASSWORD="tu_password"
```

En Linux/macOS:

```bash
export DB_USERNAME="tu_usuario"
export DB_PASSWORD="tu_password"
```

La configuración actual usa:

```text
jdbc:mysql://localhost:3306/foro_hub
```

y levanta el servidor en el puerto `8082`.

## Migraciones con Flyway

La migración inicial se encuentra en:

```text
src/main/resources/db/migration/V1__Create_Table.sql
```

Esta migración crea la tabla `posts` con los campos usados por la entidad `Post`.

## Ejecución

### Requisitos

- Java 17
- MySQL

### Windows

Desde la carpeta interna `ChallengeForoHub`:

```powershell
.\mvnw.cmd spring-boot:run
```

### Linux / macOS

```bash
./mvnw spring-boot:run
```

La API queda disponible en:

```text
http://localhost:8082/api/posts
```

## Ejemplos de uso

### Listar publicaciones

```http
GET /api/posts
```

### Crear una publicación

```http
POST /api/posts
Content-Type: application/json
```

Ejemplo de cuerpo:

```json
{
  "title": "Primer tema",
  "content": "Contenido de ejemplo",
  "author": "Sergio"
}
```

## Pruebas

El repositorio contiene actualmente una prueba básica de contexto de Spring Boot (`contextLoads`). No se incluyen todavía pruebas automatizadas de integración para los endpoints.

## Alcance y mejoras futuras

Este repositorio es un proyecto educativo de backend. Algunas mejoras razonables para una futura iteración serían:

- añadir DTOs y validaciones explícitas para requests/responses;
- implementar manejo global de errores;
- agregar endpoints de actualización y eliminación;
- incorporar autenticación/autorización;
- añadir pruebas unitarias e integración de la API;
- documentar los endpoints con OpenAPI/Swagger;
- incorporar CI para compilación y tests.

## Autor

Desarrollado por **Sergio Carey** como parte del programa de formación de **Alura Latam**.

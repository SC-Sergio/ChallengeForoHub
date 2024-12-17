ChallengeForoHub
Proyecto desarrollado por Sergio Carey para AluraLatam

Descripción del Proyecto
Este repositorio contiene un foro funcional de ejemplo desarrollado como parte del desafío solicitado por AluraLatam. El objetivo principal del proyecto fue aprender y consolidar conocimientos en el stack Spring Boot + MySQL, aplicando prácticas modernas de desarrollo.

¿Qué hace el proyecto?
Este foro permite gestionar discusiones en línea de manera eficiente, implementando funcionalidades esenciales como creación, lectura y manipulación de datos de los temas y mensajes.

¿Cómo funciona?
La aplicación está construida en Java utilizando el framework Spring Boot y sigue una arquitectura limpia organizada en tres capas principales:

Controladores: Gestionan las solicitudes HTTP y exponen los endpoints.
Servicios: Contienen la lógica del negocio y las operaciones principales.
Repositorios: Encargados de la interacción con la base de datos mediante Spring Data JPA.
La persistencia de los datos se realiza con MySQL, y para mantener el control de las versiones del esquema de la base de datos, se utiliza Flyway, que facilita la migración entre diferentes entornos y asegura una estructura coherente.

Características Principales
Seguridad en la Configuración: Las credenciales de la base de datos y configuraciones sensibles se manejan mediante variables de entorno, garantizando un código limpio y seguro.
Pruebas Eficientes: Se incluye una colección de peticiones en Insomnia para probar rápidamente los endpoints y validar su funcionamiento.
Automatización con Flyway: La creación y actualización de las tablas y esquemas se realiza automáticamente, simplificando el despliegue en distintos entornos.
Desarrollo Modular: El proyecto sigue buenas prácticas de programación, con una clara separación de responsabilidades para facilitar su mantenimiento y escalabilidad.
Tecnologías Utilizadas
Java 17
Spring Boot
MySQL
Flyway
Insomnia para pruebas
Variables de entorno para mayor seguridad

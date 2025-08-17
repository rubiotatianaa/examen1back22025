Documentación - Projecto evaluativo Primer Momento

En primer lugar, se realizó la conversión del gestor de proyectos de Gradle a Maven.
Para ello, se eliminaron los archivos y paquetes asociados a Gradle, y posteriormente se creó el archivo pom.xml, donde se configuraron las dependencias necesarias para el funcionamiento del proyecto.

Las dependencias incluidas fueron:

H2 Database: para pruebas con una base de datos en memoria.
Spring Web: para la creación de controladores y servicios web.
MySQL Connector: para la conexión con la base de datos MySQL.
Spring DevTools: para acelerar el desarrollo con reinicios automáticos.
Spring Data JPA: para la gestión de la persistencia y mapeo objeto-relacional.

Configuración de la base de datos
Se establece la conexión a la base de datos MySQL mediante las siguientes propiedades en el archivo application.properties:
spring.application.name=Examen1Back2

spring.datasource.url=jdbc:mysql://localhost:3306/develop_db
spring.datasource.username=root
spring.datasource.password=

spring.jpa.hibernate.ddl-auto=update




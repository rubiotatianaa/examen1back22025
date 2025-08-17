Documentación - Projecto evaluativo Primer Momento

En primer lugar, se realizó la conversión del gestor de proyectos de Gradle a Maven.
Para ello, se eliminaron los archivos y paquetes asociados a Gradle, y posteriormente se creó el archivo pom.xml, donde se configuraron las dependencias necesarias para el funcionamiento del proyecto.

Las dependencias incluidas fueron:

H2 Database: para pruebas con una base de datos en memoria.

Spring Web: para la creación de controladores y servicios web.

MySQL Connector: para la conexión con la base de datos MySQL.

Spring DevTools: para acelerar el desarrollo con reinicios automáticos.

Spring Data JPA: para la gestión de la persistencia y mapeo objeto-relacional.



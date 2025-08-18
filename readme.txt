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

Errores corregidos en la clase
*Curso

Al revisar la clase Curso se identificaron y corrigieron los siguientes errores:
- Error de sintaxis en la declaración de atributos
En el atributo private String nombre hacía falta una coma al final de la línea. Se realizó la corrección correspondiente.

- Falta de encapsulamiento en un atributo
El atributo de tipo Docente no tenía especificador de acceso. Se corrigió declarando la variable como:
private Docente docente;

- Constructores incompletos
La clase contaba con dos constructores: uno vacío y otro con parámetros, pero este último solo contemplaba dos atributos.
Se generó un nuevo constructor incluyendo el tercer atributo faltante para asegurar la correcta inicialización de los objetos.

Métodos de acceso faltantes
La clase no contaba con los métodos getter y setter. Se implementaron para permitir la manipulación controlada de los atributos.

--> Corrección de anotaciones

Clave primaria
Se encontró la anotación incorrecta @I, la cual fue corregida a @Id.
@Id se utiliza para identificar el campo que será la clave primaria en la tabla correspondiente.

Generación automática del identificador
En el código se encontraba la anotación incompleta @Gen(strategy = IDENTITY), lo cual generaba error.
Se realizó la corrección correspondiente a:
@GeneratedValue(strategy = GenerationType.IDENTITY)
Esta anotación permite que el campo clave primaria se genere de manera automática con la estrategia de autoincremento propia de la base de datos.

Campo nombre
Inicialmente el atributo private String nombre; no contaba con anotaciones.
Se añadió la anotación @Column para definir las características de este campo en la base de datos:
@Column(name = "nombre", nullable = false, unique = false)
private String nombre;
Con esta configuración se establece que la columna no admite valores nulos (nullable = false) y que no es un campo único (unique = false).

Llave foránea (JoinColumn)
Se detectó un error en la anotación @JoinColumn, ya que incluía un punto y coma al final:
@JoinColumn(name="fk_docente", referencedColumnName = "id");
Las anotaciones en Java no deben llevar punto y coma al final, por lo tanto, se corrigió de la siguiente manera:
@JoinColumn(name="fk_docente", referencedColumnName = "id").

*DOCENTE
En esta clase se identificaron y corrigieron varios aspectos:
La anotación @Entity estaba incompleta (@Entit), por lo que se corrigió adecuadamente.
La clave primaria no contaba con las anotaciones correspondientes, por lo que se agregaron:
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Integer id;

- El campo especialidad no estaba declarado como una columna en la base de datos. Se añadió la anotación:
@Column(name = "especialidad", nullable = false, unique = false)


- No existían constructores definidos. Se generaron los siguientes:
 public Docente() {
 }
 public Docente(Integer id, String especialidad, List<Curso> cursos, Usuario usuario) {
     this.id = id;
     this.especialidad = especialidad;
     this.cursos = cursos;
     this.usuario = usuario;
 }

- Los métodos getter y setter estaban desordenados o incompletos. Se eliminaron y se generaron nuevamente de forma ordenada para mantener una estructura clara y coherente.



# Modulo 1
- Intro a Base de datos
- Conceptos preliminares
- Modificacion de estructuras
- Insercion de base de datos

# Introduccion a Base de datos
Una base de datos es una colección organizada y estructurada de datos que sigue un modelo de información específico para reflejar sus relaciones. En la actualidad, la mayoría de las bases de datos se encuentran en formato digital debido al desarrollo tecnológico en campos como la informática y la electrónica. Esto proporciona diversas soluciones para almacenar grandes volúmenes de datos de manera eficiente.

### Motor de base de datos
Un Motor de Bases de Datos (SGBD o DBMS/RDBMS) es un sistema que permite la creación, gestión y administración de bases de datos, así como la selección y manipulación de estructuras para almacenar, buscar y gestionar información de manera eficiente. Los usuarios pueden acceder a la información a través de herramientas de consulta o aplicaciones específicas. En resumen, los motores de bases de datos sirven para definir, construir y manipular bases de datos. Algunas marcas populares incluyen ORACLE, MySQL, SQL Server, PostgreSQL y SQLite.

## Repositorio de datos
Un repositorio de datos es un lugar centralizado donde se almacena y mantiene información digital, como bases de datos o archivos informáticos. Pueden estar distribuidos a través de una red como Internet o en medios físicos. Pueden ser públicos o protegidos con autenticación. Los repositorios académicos e institucionales son comunes. A diferencia de las computadoras personales, los repositorios suelen tener sistemas de respaldo para la recuperación de datos en caso de fallas. Son fundamentales en sistemas GNU/Linux para almacenar paquetes de software disponibles para instalación.

- **Usuarios:** Personas que acceden a los datos, pueden ser finales, avanzados, desarrolladores o administradores.
- **Aplicaciones:** Utilizan el motor de base de datos para acceder a la información y presentarla al usuario. Desarrolladas en diversos lenguajes como JAVA, PHP, Visual Basic, C#, C++, Python, etc.
- **Sistemas de administración de bases de datos relacionales (RDBMS):** Software específico que actúa como interfaz entre el motor de la base de datos, la base de datos misma, los usuarios y las aplicaciones. Su propósito es gestionar datos de manera clara y ordenada para convertirlos en información relevante para la organización.
- **Dato:** Es la unidad mínima de información, sin sentido en sí misma, pero que adquiere significado en conjunto con otras precedentes de la aplicación que las creó. Es un conjunto de símbolos que, unidos de cierta forma, dan un significado lógico.

- **Definición de datos:** Realiza una descripción de la estructura de los datos (su tipología, la forma en que se relacionan, etc.), de las operaciones que pueden realizarse con ellos (añadir, eliminar, modificar, recuperar) y de las restricciones referentes a su integridad (aquellas condiciones que todos los datos deben respetar para que la información sea válida, consistente y congruente).


### MySQL

MySQL es un SGBD multihilo y multiusuario utilizado en la gran parte de las páginas web actuales. Además, es el más usado en aplicaciones creadas como software libre. Se ofrece bajo la GNU GPL, aunque también es posible adquirir una licencia para empresas que quieran incorporarlo en productos privativos.


### Ventajas

Las principales ventajas de MySQL como Sistema Gestor de Bases de Datos son:

- Facilidad de uso y gran rendimiento.
- Facilidad para instalar y configurar.
- Soporte multiplataforma.
- Soporte SSL.

### Desventajas

La principal desventaja es la escalabilidad, es decir, no trabaja de manera eficiente con bases de datos muy grandes que superan un tamaño determinado.


### ¿Qué es SQL?

SQL significa Structured Query Language (Lenguaje Estructurado de Consultas), el cual puede referirse como lenguaje de programación o lenguaje de consulta. El objetivo principal de SQL es interactuar con la base de datos relacional en la que se almacenan los datos de forma tabular (tabla formada por filas y columnas).

El motor recopila e interpreta comandos y/o sentencias SQL para que se puedan realizar las operaciones apropiadas en la base de datos relacional. El objetivo del motor SQL es crear (Create), leer (Read), actualizar (Update) y eliminar datos (Delete): CRUD de una base de datos.

Existen varios tipos de motores SQL y todos tienen una arquitectura diferente, pero realizan el mismo objetivo que incluye operaciones CRUD en la base de datos y muchas otras características.


### TIPOS DE SENTENCIAS 
| TIPO | SENTENCIA | ACCIÓN |
|------|-----------|--------|
| DML  | SELECT    | Recupera datos de una o varias tablas |
|      | INSERT    | Inserta nuevas filas en una tabla |
|      | UPDATE    | Actualiza datos existentes en una tabla |
|      | DELETE    | Elimina filas de una tabla |
|------|-----------|--------|
| DDL  | CREATE    | Crea un objeto (Database, table, view, etc) |
|      | ALTER     | Modifica un objeto (Database, table, view, etc) |
|      | DROP      | Elimina un objeto (Database, table, view, etc) |
|------|-----------|--------|
| DCL  | GRANT     | Asigna permisos/privilegios de acceso a un objeto |
|      | REVOKE    | Revoca/quita permisos/privilegios de acceso a un objeto |
|------|-----------|--------|
| DCL  | START     | Inicia una transacción |
|      | COMMIT    | Confirma el resultado de una transacción |
|      | ROLLBACK  | Deshace el resultado de una transacción |
|------|-----------|--------|
| PL-SQL | DECLARE | Crea un cursor a partir los resultados de una consulta |
|        | OPEN    | Abre un cursor para recuperar los resultados |
|        | FETCH   | Recupera una fila desde los resultados |
|        | CLOSE   | Cierra un cursor |
|        | Etc.    | Incluye sentencias de control de flujo (If, Case, While, etc.) |


### Control de concurrencias
El control de concurrencia es esencial en los sistemas de bases de datos debido a la simultaneidad de servicios para múltiples usuarios y desarrolladores que acceden desde fuera de la máquina donde reside la base de datos (a través de red local, Internet, Intranet, etc.). Se encarga de garantizar la consistencia de cada operación (transacción) y prevenir conflictos al realizar operaciones de escritura en el mismo registro simultáneamente.

# Conceptos preliminares
### Tablas
- Las tablas son el objeto principal de una base de datos, donde se almacenan los datos.
- Son estructuras que almacenan información relacionada sobre algún objeto o entidad.
- Cada tabla tiene un nombre único en toda la base de datos.
- Están compuestas por registros (filas) y campos (columnas).
- Los registros y campos pueden ordenarse de manera diferente.
- Una base de datos puede contener múltiples tablas.


### Tipos de datos
| Tipo          | Descripción                                                                                      |
|---------------|--------------------------------------------------------------------------------------------------|
| **Caracteres o cadenas de texto**                                                                    |
| CHAR          | Se utiliza para almacenar cadenas de longitud fija. Su longitud abarca desde 1 a 255 caracteres. |
| VARCHAR       | Similar a CHAR, pero de longitud variable, solo almacena la longitud del dato.                  |
| TINYTEXT      | Texto de longitud variable que puede tener hasta 255 caracteres.                                  |
| TEXT          | Texto de longitud variable que puede tener hasta 65,535 caracteres.                                |
| MEDIUMTEXT    | Texto de longitud variable que puede tener hasta 16,777,215 caracteres.                            |
| LONGTEXT      | Texto de longitud variable que puede tener hasta 4,294,967,295 caracteres.                         |
| BLOB          | Dato binario para almacenar archivos o texto.                                                     |
| **Datos numéricos**                                                                                 |
| BIT o BOOL    | Para un número entero que puede ser 0 o 1.                                                        |
| TINYINT       | Número entero con rango de valores desde -128 a 127.                                              |
| SMALLINT      | Números enteros con rango desde -32,768 a 32,767.                                                  |
| MEDIUMINT     | Números enteros con rango desde -8,388,608 a 8,388,607.                                            |
| INT           | Números enteros con rango desde -2,147,483,648 a 2,147,483,647.                                    |
| BIGINT        | Número entero con rango de valores desde -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807.  |
| FLOAT         | Números decimales.                                                                              |
| DOUBLE        | Número de coma flotante de precisión doble.                                                      |
| DECIMAL       | Almacena los números como cadenas de texto.                                                       |
| **Fecha**                                                                                            |
| DATE          | Para almacenar fechas.                                                                           |
| DATETIME      | Combinación de fecha y hora.                                                                     |
| TIME          | Almacena una hora.                                                                               |
| YEAR          | Almacena un año.                                                                                 |

### Creacion de una base de datos
Para crear una base de datos (por ejemplo, con el nombre ComercioIT), la instrucción SQL a ejecutar será:
```SQL
CREATE DATABASE ComercioIT;
```

### Creación de una tabla
La sentencia CREATE TABLE creará una tabla con las columnas (campos) que indiquemos.
```SQL
CREATE TABLE Nombre_Tabla
```

Ejemplos: 
```sql
CREATE TABLE Productos(
idProducto INT(11) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
Nombre VARCHAR(50) NOT NULL,
Precio DOUBLE,
Marca VARCHAR(30) NOT NULL,
Categoria VARCHAR(30) NOT NULL,
Stock INT(6) NOT NULL,
Disponible BOOLEAN DEFAULT false
);
```

### Eliminar una tabla
Para eliminar una tabla (por ejemplo, con el nombre Productos) de una base de datos, la instrucción SQL a ejecutar será:
```sql
DROP TABLE Productos;
o
DROP TABLE IF EXISTS Productos;
```

### Restricciones de las tablas
### Puntos Claves:
1. Los nombres de las tablas deben ser únicos en la base de datos.
2. Los nombres de las columnas deben ser únicos en la tabla.
3. No pueden existir dos registros con el mismo valor de la clave primaria.

### Columnas no descomponibles:
1. Contienen información que no puede dividirse en dos o más columnas.
2. Son fáciles de actualizar y consultar.
3. Mejoran la integridad de los datos.

### Modificadores aplicables a los campos de una tabla:
- **NOT NULL:** Obliga a que se ingrese un valor en el campo, no puede quedar vacío.
- **DEFAULT:** Especifica un valor predeterminado para el campo.
- **PRIMARY KEY:** Identifica de forma única a cada registro de la tabla.
- **UNIQUE:** Asegura que los valores en la columna sean únicos, permitiendo valores nulos.
- **BINARY:** Almacena los valores en modo binario, respetando mayúsculas y minúsculas.
- **UNSIGNED:** Indica que la columna solo almacena números positivos.
- **ZERO FILL:** Completa el campo con ceros si es numérico.
- **AUTO_INCREMENT:** El motor de base de datos incrementa automáticamente su valor. Se aplica generalmente en la clave primaria y solo puede haber una por tabla.


### Otros comandos MySQL
- **Comando SHOW DATABASES:** Muestra el catálogo de base de datos del servidor.
    ```
    SHOW DATABASES;
    ```
- **Comando USE:** Pone en uso una base de datos del servidor. Todos los comandos SQL que se ejecuten, se llevarán a cabo sobre la base de datos en uso.
    ```
    USE NombredeBaseDeDatos;
    ```

- **Comando SHOW TABLES:** Muestra el catálogo o listado de tablas de la base de datos activa.
    ```
    SHOW TABLES;
    ```
- **Comentarios:** Permiten escribir texto que no será interpretado como parte de sentencias SQL, útiles para documentar y comentar acciones realizadas por las sentencias. Se pueden utilizar las siguientes formas de escribir comentarios:
    - Esto es un comentario de 1 línea (Propia de MySQL)
    ```
    # Esto es un comentario de 1 línea
    ```
    - Esto es un comentario de 1 o más líneas (Soportada en MySQL y otros motores)
    ```
    /* Esto es un comentario de 1 o más líneas */
    ```
    - Esto es un comentario de 1 línea (Soportada en MySQL y otros motores)
    ```
    -- Esto es un comentario de 1 línea
    ```

- **Comando DESCRIBE:** Devuelve la descripción de campos y detalles de una tabla (estructura física).
- **Comando SHOW CHARSET:** Muestra los CHARSET (juegos de caracteres).
- **Comando SHOW COLLATION:** Muestra los COLLATIONS instalados.

### ENUM
- Sólo puede contener un valor.
- Se puede definir una lista de hasta 65.535 valores distintos.
- Si se permiten valores null, éste será el valor predeterminado; si no se define un valor predeterminado con DEFAULT, será el primer valor de la lista.
- Cada valor de la lista es numerado con un índice (comenzando en 1).

Ejemplo de uso:
```sql
CREATE TABLE Medida (
    medida ENUM('pequeño', 'mediano', 'grande') NOT NULL DEFAULT 'mediano'
);
```
### SET
- Puede contener 0, 1 o varios valores.
- Se puede definir una lista de hasta 64 valores distintos.
- Los valores no pueden contener comas, ya que los valores asignados en la lista están separados por ese carácter.
- Cada valor de la lista representa un bit de la cadena de bits del campo.
- El valor decimal del campo determina los bits, al marcar los valores que contiene el campo. Por ejemplo, si el valor decimal es 7, en binario sería 0111, lo que significa que el campo contiene los valores 'a', 'b' y 'c'.
```sql
CREATE TABLE Letra (
    letra SET('a', 'b', 'c', 'd')
);
```

# Modificacion de estructuras
### ALTER TABLE
Este comando permite modificar la estructura de una tabla. Se utiliza para agregar o eliminar columnas, modificar el tipo de datos de una columna existente o renombrar una columna o una tabla.

En el ejemplo siguiente, se agrega una nueva columna con el nombre Observaciones a una tabla llamada articulos:
```sql
ALTER TABLE articulos ADD COLUMN Observaciones VARCHAR(50) NULL;
```

### Agregar columnas a una tabla
En el siguiente ejemplo, se agrega una nueva columna con el nombre Primera a una tabla llamada clientes. Se coloca al comienzo de la tabla:
```sql
ALTER TABLE clientes ADD COLUMN Primera VARCHAR(50) NULL FIRST;
```

### Agregar columna entre columnas existentes
En el siguiente ejemplo, se agrega una nueva columna con el nombre Siguiente a una tabla llamada clientes, entre las columnas Nombre y Apellido:
```sql
ALTER TABLE clientes ADD COLUMN Siguiente VARCHAR(50) NULL AFTER Nombre;
```

### Cambiar el nombre de una columna
En el siguiente ejemplo, se modifica el nombre de la columna observaciones por comentarios en la tabla articulos:
```sql
ALTER TABLE articulos CHANGE observaciones comentarios VARCHAR(40) NULL;
```

### Cambiar el tipo de dato de una columna
En el siguiente ejemplo, se modifica el tipo de dato de la columna comentarios en la tabla articulos:
```sql
ALTER TABLE articulos MODIFY comentarios TEXT NULL;
```

### Eliminar una columna
En el siguiente ejemplo, se elimina la columna comentarios de la tabla articulos:
```sql
ALTER TABLE articulos DROP COLUMN comentarios;
```

Y en el siguiente ejemplo, se eliminan las columnas Primera y Siguiente de la tabla clientes, en una sola sentencia:
```sql
ALTER TABLE clientes DROP COLUMN Primera, DROP COLUMN Siguiente;
```
### Renombrar una tabla
En el siguiente ejemplo, se modifica el nombre de la tabla Articulos por Productos:
```sql
ALTER TABLE Articulos RENAME Productos;
```
Otra forma de cambiar el nombre de una tabla es:
```sql
RENAME TABLE Articulos TO Productos;
```
### Agregar y eliminar restricciones
En el siguiente ejemplo, se elimina la restricción Primary Key de la tabla Articulos:
```sql
ALTER TABLE Articulos DROP PRIMARY KEY;
```
En el siguiente ejemplo, se agrega la restricción Primary Key al campo ArticuloID en la tabla Articulos:
```sql
ALTER TABLE Articulos ADD PRIMARY KEY (ArticuloID);
```
### Eliminar y agregar restricciones FOREIGN KEY
En el siguiente ejemplo, se elimina la restricción FOREIGN KEY del campo fk_articulo de la tabla facturas:
```sql
ALTER TABLE facturas DROP FOREIGN KEY fk_articulo;
```
Y en el ejemplo siguiente, se agrega la restricción FOREIGN KEY al campo fk_articulo de la tabla facturas:
```sql
ALTER TABLE facturas ADD CONSTRAINT fk_articulo FOREIGN KEY (ArticuloID) REFERENCES Articulos(ArticuloID);
```

# Insercion de base de datos
### Insertar registros en una tabla
Para insertar datos en una tabla utilizamos la sentencia INSERT. Con ella, podemos añadir registros uno a uno o tantos registros como deseemos en una sola sentencia. Existen distintas formas de ingresar registros en una tabla, reconocidas con los siguientes nombres:

#### Manera completa
```sql
INSERT INTO PRODUCTOS (Nombre, Precio, Marca, Categoria, Stock, Disponible) VALUES ('iPhone 5', 499.99, 'Apple', 'Smartphone', 500, false);
```
En este caso, después del nombre de la tabla, se deben especificar los campos contenidos en la tabla. Posteriormente, se especifican los valores a cargar en cada uno de ellos.

### Manera SQL
```sql
INSERT INTO PRODUCTOS SET Nombre = 'iPhone 5', Precio = 499.99, Marca = 'Apple', Categoria = 'Smartphone', Stock = 500, Disponible = false;
```
En este caso, los datos a cargar o insertar en cada uno de los campos se definen junto a su nombre. Es solo una manera distinta de insertar el registro en la tabla PRODUCTOS.

### Manera simplificada
```sql
INSERT INTO Productos
VALUES ('iPhone 5', 499.99, 'Apple', 'Smartphone', 500, false)
```
En este caso, sólo se especifican los valores a cargar en cada uno de los campos. Se la denomina manera simplificada, dado que no se especifican los nombres de los campos luego del nombre de la tabla. Sólo se detallan los datos a cargar en cada campo de la tabla. Es muy importante respetar el orden; los datos se deben especificar en el mismo orden en que figuran las columnas en la tabla.

### Valores nulos: NULL

La expresión `NULL` significa "dato desconocido" o "valor inexistente". No es lo mismo que un valor 0 en un campo numérico, o una cadena vacía, o una cadena de texto con la palabra NULL literal en un campo de tipo texto.

A veces, puede desconocerse o no existir el dato correspondiente a algún campo de un registro. En estos casos, se dice que el campo puede contener valores nulos.

Por ejemplo, en una tabla con el nombre Productos, se puede tener valores nulos en el campo precio, en el caso de que, para algunos productos, no se haya establecido el precio para la venta.

En contraposición, una tabla puede contener campos que no pueden quedar vacíos, como los campos que identifican cada registro (códigos de identificación), que son clave primaria.

Nota: Por defecto (si no lo aclaramos en la creación de la tabla) los campos permiten valores nulos.

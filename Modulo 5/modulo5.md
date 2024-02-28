# Modulo 5
- Subconsultas 
- Condicional CASE
- Combinacional de consultas 
- Consultas reacionadas 

# Subconsultas
Una subconsulta es una consulta, es decir, un SELECT dentro de otra consulta (otro SELECT). Su objetivo es obtener un resultado y utilizarlo como criterio de búsqueda para obtener un determinado listado de registros.

El siguiente ejemplo utiliza una subconsulta para conocer todos los registros de la tabla `articulos` cuyo valor de campo `articuloID` se encuentra en el campo `articuloID` de la tabla `facturas`.

```sql
SELECT * FROM articulos WHERE articuloID IN (SELECT articuloID FROM facturas);
```
### Subconsulta Escalar

Se denomina subconsulta escalar a aquella subconsulta que devuelve un único resultado (como puede ser una suma, un promedio, un valor máximo, un valor mínimo, etc.).

En el ejemplo siguiente, se define una consulta que devuelve de la tabla `alumnos` a todos aquellos alumnos cuya edad supera la edad promedio. La subconsulta calcula dicho promedio y la consulta principal toma ese resultado como criterio de búsqueda, mostrando todos los registros de la tabla `alumnos` que cumplan con el criterio establecido.

```sql
SELECT * FROM alumnos WHERE edad > (SELECT AVG(edad) FROM alumnos);
```

# Condicional CASE
El condicional CASE permite asignar un valor a una columna tomando como referencia otro valor de la tabla. Por cada valor o grupo de valores existe un `WHEN` y un `THEN`; si encuentra un valor coincidente en algún `WHEN`, ejecuta el `THEN` correspondiente a ese `WHEN`; caso contrario, se ejecuta el `ELSE`. Este condicional se debe cerrar con la palabra `END` para indicar que el `CASE` ha finalizado.

```sql
CASE WHEN precio < 20 THEN 'BARATO'
```
El siguiente ejemplo asigna un posible valor (`CARO` / `BARATO` / `EQUILIBRADO`) en una columna con el nombre `Categoria`, tomando como referencia los valores de la columna `precio` de una tabla con el nombre `articulos`.
```sql
SELECT nombre, precio,
CASE
WHEN precio < 20 THEN 'BARATO'
WHEN precio BETWEEN 20 AND 40 THEN 'EQUILIBRADO'
ELSE 'CARO'
END as Categoria
FROM articulos;
```

# Combinación de consultas: UNION
Para comparar los resultados de varias consultas y combinarlos en un nuevo resultado basado en esa comparación existe (entre otros) el operador UNION. Dado que se compararán varias consultas, es necesario que:

- en cada resultado exista la misma cantidad de campos y
- los campos a comparar tengan tipos de datos compatibles (no es necesario que tengan el mismo nombre).

Las dos consultas se pueden hacer sobre la misma tabla, pero podría ser cualquier consulta siempre y cuando se respete que la salida contenga la misma cantidad de campos y que los tipos de datos de los campos sean compatibles para la comparación; en general, esto implica campos numéricos con campos numéricos y campos de texto con campos de texto.

### UNION - UNION ALL
La sintaxis para combinar dos consultas mediante la cláusula UNION es:
```SQL
consulta1 UNION [ALL] consulta2;
```
Esta sintaxis agrega el resultado de la consulta2 al resultado de la consulta1. Los registros que quedan duplicados, se eliminan (no se muestran en el resultado). Para conservar los registros duplicados, se utiliza la cláusula UNION ALL en lugar de UNION.

### Ejemplos de combinación de consultas

#### Ejemplo 1
Se necesita obtener una lista completa de todos los bebés nacidos en el año 2020 en la República Argentina. La sentencia SQL sería la siguiente:
```SQL
SELECT * FROM nenes
UNION
SELECT * FROM nenas;
```

#### Ejemplo 2
En el siguiente ejemplo, se suponen las mismas tablas que en el caso anterior. Y se necesita obtener una lista completa de todos los bebés nacidos en el año 2020 en la República Argentina, en la provincia de Córdoba. La sentencia SQL sería la siguiente:
```SQL
SELECT * FROM nenes WHERE provincia = 'Córdoba'
UNION
SELECT * FROM nenas WHERE provincia = 'Córdoba';
```

#### Ejemplo 3
Ahora, se suponen las mismas tablas que en el caso anterior. Y se necesita obtener una lista completa de todos los bebés nacidos en el año 2020 en la República Argentina: bebés de sexo masculino nacidos en la provincia de Córdoba y bebas de sexo femenino nacidas en la provincia de La Pampa. La sentencia SQL sería:
```SQL
SELECT * FROM nenes WHERE provincia = 'Córdoba'
UNION
SELECT * FROM nenas WHERE provincia = 'La Pampa';
```

#### Ejemplo 4
En este último ejemplo, se suponen las mismas tablas que en el caso anterior. Y se necesita obtener una lista completa de todos los bebés nacidos durante el mes de agosto del año 2020 en la República Argentina. La sentencia SQL sería la siguiente:
```SQL
SELECT * FROM nenes WHERE MONTH(fecha_nacimiento) = 8
UNION
SELECT * FROM nenas WHERE MONTH(fecha_nacimiento) = 8;
```

# Consultas relacionadas
### Consultas de más de una tabla

Es posible consultar datos desde varias tablas en la misma sentencia SELECT. Esto permite realizar otras dos operaciones de álgebra relacional: el producto cartesiano y la composición interna.

#### Producto cartesiano

Se obtiene mencionando las dos tablas en una consulta sin ninguna restricción en la cláusula WHERE. El producto cartesiano de dos tablas son todas las combinaciones de todas las filas de las dos tablas. Usando una sentencia SELECT se deben listar todos los campos de ambas tablas. Los nombres de las tablas se indican en la cláusula FROM separados con comas.

Ejemplo:
```sql
SELECT * FROM Productos, Marcas;
```

#### Composición interna

La composición interna se trata de un producto cartesiano restringido en donde las tuplas (conjunto de nombres de atributos relacionados) que se emparejan deben cumplir una condición determinada.

Ejemplo:
```sql
SELECT * FROM Productos, Marcas
WHERE Productos.Marca = Marcas.idMarca;
```


### Modelo Entidad - Relación Introducción

Cuando se utiliza una base de datos para gestionar información, se está plasmando una parte del mundo real en una serie de tablas, registros y campos ubicados en un dispositivo, lo cual crea un modelo parcial de la realidad. Antes de crear físicamente estas tablas, se debe realizar un modelo de datos.

#### Entidad

Una entidad es cualquier "objeto" discreto sobre el que se tiene información. Cada ejemplar de una entidad se denomina instancia. Las entidades son modeladas en la base de datos como tablas.

#### Integridad referencial

La integridad referencial es un mecanismo que garantiza la integridad de datos en tablas relacionadas, ya que la misma evita la existencia de los llamados registros huérfanos (registros hijos sin su correspondiente registro padre).

#### Clave Foránea (Foreign Key)

La Clave Foránea de una tabla es aquella que referencia a la Clave Primaria de una tabla. Ésta puede referenciar a la Clave Primaria de la misma tabla o de otra. Ante una consulta SQL, se valida la legitimidad de los datos almacenados en una Clave Foránea y se fuerza la integridad referencial.

Ejemplo de sintaxis:
```sql
ALTER TABLE Facturas ADD FOREIGN KEY(id_articulo) REFERENCES Articulos(id_articulo) ON DELETE CASCADE ON UPDATE CASCADE;
```

#### Súper llave

Es un conjunto de uno o más atributos que "juntos" permiten identificar de forma única un registro en el conjunto de registros. Este tipo de llaves contiene comúnmente atributos ajenos, es decir, atributos que no son indispensables para llevar a cabo el reconocimiento del registro.

#### Conceptos clave

- **Clave candidata**: es una súper llave mínima. Una tabla puede tener varias llaves candidatas, pero solo una es elegida como llave primaria.
- **Relación**: una relación describe cierta interdependencia (de cualquier tipo) entre una o más entidades. Esta no tiene sentido sin las entidades que relaciona. Las relaciones son definidas con claves primarias y claves foráneas y mantienen la integridad referencial.
- **Cardinalidad de las Relaciones**: una relación describe cierta interdependencia (de cualquier tipo) entre una o más entidades. Las relaciones pueden ser:
  - De uno a uno
  - De uno a muchos
  - De muchos a muchos

#### Consideraciones en el planeamiento del Diseño Lógico de la Base de Datos

- Determinar el negocio y las necesidades del usuario.
- Considerar cuáles son los problemas que hay que resolver y las tareas que los usuarios deberán completar.
- Crear Bases de Datos Normalizadas.
- Evitar el almacenamiento de información duplicada, inconsistencias en la base de datos, anomalías y problemas de pérdida de la información.

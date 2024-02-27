# Modulo 2
- Importacion de tablas
- Consultar tablas
- Predicado de consultas SQL 

# Importar tablas desde orígenes externos

En muchas ocasiones, una empresa puede tener tablas generadas en Microsoft Access o Microsoft Excel y, debido a la cantidad de información que contienen, se decide migrarlas a SQL para una mejor gestión. MySQL Workbench permite la importación de tablas desde archivos externos, aunque solo admite archivos en formato CSV o JSON.

Dado que estas tablas no fueron generadas en SQL, los campos pueden no tener definidos tipos de datos ni modificadores. Al importar las tablas, se puede especificar el tipo de dato para cada campo utilizando el comando ALTER TABLE.

#### Mecanismo de importación

Para importar tablas desde archivos CSV o JSON:

1. Haz clic derecho en el nombre de la base de datos en uso.
2. Selecciona la opción "Table Data Import Wizard".
3. Haz clic en "Browse" y selecciona el archivo que contiene la tabla a importar.
4. Haz clic en "Next".
5. Especifica si deseas volcar los datos en una tabla existente o crear una nueva tabla.
6. En este paso, puedes definir los tipos de datos para cada campo.
7. Una vez definidos los tipos de datos, haz clic en "Next".
8. Confirma la importación de los datos y haz clic en "Next" para comenzar la importación.
9. Una vez finalizada la importación, haz clic en "Next" para ver los detalles y luego en "Finish" para concluir el asistente.
10. Actualiza los esquemas para ver la tabla importada en la base de datos.

### Generar tablas desde scripts

Si cuentas con un archivo SQL que contiene un script para generar una tabla, puedes abrirlo desde el motor de base de datos y ejecutarlo para crear la tabla en la base de datos en uso.

#### Pasos para generar tablas desde scripts:

1. Abre MySQL Workbench.
2. Ejecuta el comando "File Open SQL Script".
3. Ubica y abre el archivo SQL que contiene el script para generar la tabla.
4. Ejecuta el script.
5. Actualiza los esquemas para ver la tabla recién creada en la base de datos.

# Consultar tablas
La sentencia SELECT permite realizar operaciones de selección, ordenación, agrupación y filtrado de registros. Esta instrucción o sentencia utiliza diversas cláusulas:
| Cláusula | Descripción                                                                                     |
|----------|-------------------------------------------------------------------------------------------------|
| FROM     | Especifica la tabla de la que se quieren obtener los registros.                                  |
| WHERE    | Especifica los criterios o condiciones que deben cumplir los registros a buscar dentro de la tabla. |
| GROUP BY | Permite agrupar los registros seleccionados en función de uno o más campos.                         |
| HAVING   | Especifica las condiciones que deben cumplir los grupos generados.                               |
| ORDER BY | Ordena los registros seleccionados en función de un campo.                                        |

### Mostrar todo el contenido de una tabla

En el ejemplo de la derecha, se selecciona de la tabla Articulos todos los registros contenidos en la tabla y se muestran todas las columnas.
El asterisco (*) ubicado a continuación de la sentencia SELECT especifica que, en el resultado de la consulta, se deben mostrar todas las columnas (campos) contenidos en la tabla.
Nota: En este ejemplo, sólo se hace uso de la cláusula FROM. No se utilizan todas las otras cláusulas, ya que el objetivo final era obtener un listado de todos los registros contenidos en la tabla.

```sql
SELECT * FROM Articulos;
```

### Mostrar algunos campos de una tabla
En el siguiente ejemplo, se selecciona de la tabla Articulos los valores de la columna Nombre, de todos los registros contenidos en la tabla:
```sql
SELECT Nombre FROM Articulos;
```
Y en el siguiente ejemplo, se selecciona de la tabla Articulos todos los valores de las columnas Nombre y Precio, de todos los registros contenidos en la tabla:
```sql
SELECT Nombre, Precio FROM Articulos;
```

### Generar columnas en una consulta
En el siguiente ejemplo, se selecciona de la tabla Articulos los valores de todas las columnas y se agrega una nueva columna con el nombre Precio con Aumento, al incrementar en un 25% el valor de la columna Precio:
```sql
SELECT *, Precio * 1.25 as ‘Precio con Aumento’ FROM Articulos;
```
Y en el siguiente ejemplo, se selecciona de la tabla Articulos los valores de todas las columnas y agrega una nueva columna con el nombre Origen, con el valor constante China:
```sql
SELECT *, ‘China’ as Origen FROM Articulos;
```
### Ordenamiento de datos: cláusula ORDER BY
La cláusula ORDER BY tiene como finalidad ordenar los resultados de las consultas por otras columnas. Cuando se genera un SELECT en base a una tabla, el resultado siempre se muestra ordenado en base al campo índice (PRIMARY KEY) por defecto.
Tenga en cuenta que:
- El orden puede ser ascendente (por defecto) o descendente.
- Se puede ordenar por una columna o un conjunto de ellas
En el siguiente ejemplo, se ordena el resultado de la consulta por el campo apellido (por defecto, en orden ascendente)
```sql
SELECT nombre, apellido FROM clientes ORDER BY apellido; -- ASC
```
Y en el siguiente ejemplo, se ordena el resultado de la consulta por el campo apellido (por defecto, en orden ascendente) y por el campo nombre en orden descendente:
```sql
SELECT nombre, apellido FROM clientes ORDER BY apellido, nombre DESC;
```

### Limitar la cantidad de registros

Para limitar el número de filas (registros/resultados) devueltos en una consulta generada a través de la sentencia SELECT, se debe utilizar la cláusula LIMIT. Esta cláusula también permite establecer el número máximo de registros a eliminar en el caso de utilizar la sentencia DELETE.

En el siguiente ejemplo, se limita a 2 el número total de registros a mostrar en el resultado de la consulta:

```sql
SELECT nombre, apellido FROM clientes LIMIT 2;
```
### OFFSET
La cláusula OFFSET opera en combinación con la cláusula LIMIT y permite posicionarse en el registro indicado. Mientras que LIMIT seleccionará la cantidad de registros establecidos en la sentencia, OFFSET indica desde qué registro comenzar a mostrar los resultados.

En el ejemplo siguiente, se limita a 2 el número total de registros a mostrar en el resultado de la consulta, comenzando desde el quinto registro (es decir, salteando los primeros cuatro):
```sql
SELECT nombre, apellido FROM clientes LIMIT 2 OFFSET 4;
```

# Predicado de consultas SQL 

### Cláusula WHERE
La cláusula WHERE permite especificar las condiciones o criterios que deben cumplir los registros a buscar dentro de una tabla.
| Cláusula      | Descripción                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------|
| FROM          | Especifica la tabla de la que se quieren obtener los registros.                              |
| WHERE         | Permite especificar las condiciones o criterios que deben cumplir los registros a buscar.    |
| GROUP BY      | Permite agrupar los registros seleccionados en función de uno o más campos.                  |
| HAVING        | Especifica las condiciones que deben cumplir los grupos generados.                            |
| ORDER BY      | Ordena los registros seleccionados en función de un campo.                                    |

Al especificar condiciones de búsqueda dentro de una tabla, se utilizará la cláusula WHERE, la cual se debe colocar obligatoriamente después de la cláusula FROM.


### Operadores de comparación
| Operador | Descripción          |
|----------|----------------------|
| =        | Igual a              |
| <        | Menor que            |
| >        | Mayor que            |
| >=       | Mayor o igual que    |
| <=       | Menor o igual que    |
| <>       | No es igual a        |

En el siguiente ejemplo, se selecciona de la tabla Articulos la columna Nombre y muestra todos aquellos registros cuyo valor en la columna codigo sea igual a 1:

```sql
SELECT Nombre FROM Articulos WHERE codigo = 1;
```
Y en el siguiente ejemplo, se selecciona de la tabla Articulos las columnas Nombre y Precio y muestra todos aquellos registros cuyo precio sea superior a 150:
```sql
SELECT Nombre, Precio FROM Articulos WHERE Precio > 150;
```

### Operadores lógicos
| Operador | Descripción                                        |
|----------|----------------------------------------------------|
| AND      | Se deben cumplir todas las condiciones especificadas |
| OR       | Se debe cumplir al menos una de las condiciones especificadas |
| NOT      | No debe cumplir las condiciones especificadas      |

En el siguiente ejemplo, se selecciona de la tabla Articulos todos aquellos registros cuyo precio tenga un valor mayor o igual a 500, o su stock sea mayor o igual a 100:

```sql
SELECT * FROM Articulos WHERE precio >= 500 OR stock >= 100;
```
Y en el siguiente ejemplo, se selecciona de la tabla Articulos todos aquellos registros cuyo precio tenga un valor menor a 20 y su stock sea mayor o igual a 100:
```sql
SELECT * FROM Articulos WHERE Precio < 20 AND stock >= 100;
```

### Operadores BETWEEN / NOT BETWEEN

El operador BETWEEN se utiliza para comprobar si una expresión está comprendida en un determinado rango de valores. La sintaxis es:

```sql
SELECT * FROM Articulos WHERE precio BETWEEN 100 AND 200;
```
El operador NOT BETWEEN se utiliza para comprobar si una expresión no está comprendida en un determinado rango de valores. La sintaxis es:

```sql
SELECT * FROM Articulos WHERE precio NOT BETWEEN 100 AND 200;
```

### Operadores IN / NOT IN

Los operadores IN y NOT IN se utilizan para averiguar si el valor de una expresión determinada se encuentra dentro o fuera de un conjunto especificado.

Sintaxis:
- IN (<expr1>, <expr2>, <expr3>,...)
- NOT IN (<expr1>, <expr2>, <expr3>,...)

El operador IN devuelve un valor verdadero si el valor de la expresión es igual a alguno de los valores especificados en la lista.
El operador NOT IN devuelve un valor falso en el caso contrario.

Ejemplo 1:
```sql
SELECT * FROM Articulos WHERE codigo IN (1,2,3);
```
Ejemplo 2:
```sql
SELECT * FROM Articulos WHERE nombre IN ('Pala', 'Maza');
```
Ejemplo 3
```sql
SELECT * FROM Articulos WHERE nombre NOT IN ('Pala', 'Maza');
```

### Operadores LIKE / NOT LIKE

El operador LIKE se utiliza para hacer comparaciones entre cadenas y patrones. El resultado es verdadero (1) si la cadena se ajusta al patrón y falso (0) en caso contrario. Tanto si la cadena como el patrón son NULL, el resultado es NULL. Para definir estos patrones, se hace uso de comodines, como se muestra a continuación:

- %: Coincide con cualquier número de caracteres, incluso ninguno.
- _: Coincide con un único carácter.

En el ejemplo siguiente, se muestran de la tabla Articulos todos aquellos registros en los que el campo nombre contiene la palabra "Pala":

```sql
SELECT * FROM Articulos WHERE nombre LIKE '%Pala%';
```

Como siempre que se utilizan caracteres concretos para crear patrones, se presenta la dificultad de hacer comparaciones cuando se deben buscar precisamente esos caracteres concretos. La comparación es independiente del tipo de los caracteres. Es decir, LIKE no distingue mayúsculas de minúsculas, salvo que se indique lo contrario.

Secuencias de escape: ''
La dificultad mencionada se suele superar mediante secuencias de escape. Si no se especifica nada en contra, el carácter que se usa para escapar es ''. De este modo, si queremos que nuestro patrón contenga los caracteres '%' o '_', los escaparemos de este modo: '%' y '_'.

```sql
SELECT * FROM clientes WHERE mail LIKE '%\_%';
```

### Operadores IS NULL / IS NOT NULL

Los operadores IS NULL e IS NOT NULL sirven para verificar si una expresión determinada es o no nula.

En el siguiente ejemplo, se muestran todos aquellos registros de la tabla clientes que no tengan cargado ningún valor en el campo comentarios:

```sql
SELECT * FROM clientes WHERE comentarios IS NULL;
```
Y en el siguiente ejemplo, se muestran todos aquellos registros de la tabla clientes que tengan algún valor cargado en el campo comentarios:

```sql
SELECT * FROM clientes WHERE comentarios IS NOT NULL;
```
# Modulo 4
- Creacion de tablas
- Consultas de agregacion
- Consultas de datos anexos
- Consultas de eliminacion

# Creación de Tablas con` CREATE TABLE`
Puedes crear una nueva tabla en una base de datos utilizando la sentencia CREATE TABLE. Esta sentencia te permite duplicar la estructura completa de una tabla existente o solo una parte de ella. A continuación, se muestra cómo se hace:

Ejemplo: Duplicar una Tabla Existente
```SQL
CREATE TABLE Clientes_Copia 
SELECT * FROM Clientes;
```
Este ejemplo crea una nueva tabla llamada Clientes_Copia que incluye todos los registros de la tabla original Clientes.

Ejemplo: Copiar Registros con una Condición Específica
```SQL
CREATE TABLE Clientes_Argentina 
SELECT * FROM Clientes WHERE Pais = 'Argentina';
```
Este ejemplo genera una nueva tabla llamada Clientes_Argentina que contiene solo los registros de la tabla original Clientes donde el campo Pais es 'Argentina'.

Nota: En ambos ejemplos, se replica la estructura de la tabla original y el tipo de datos de cada campo, pero no se copia la Primary Key

# Consulta de actualización
### Modificar Registros de una Tabla: DML UPDATE

Para modificar registros de una tabla en una base de datos, se utiliza la sentencia UPDATE. La sintaxis general del comando UPDATE para actualizar un registro existente es la siguiente:

```sql
UPDATE Tabla SET Campo1 = Valor1 WHERE Campo = 'Valor';
```

También es posible actualizar el valor de más de una columna separándolas en la sección SET mediante comas como delimitador:

```sql
UPDATE Tabla SET Campo1 = Valor1, Campo2 = Valor2 WHERE Campo = 'Valor';
```

#### Actualizaciones Selectivas con la Cláusula WHERE

Mediante la cláusula WHERE se puede establecer una condición para que solo las filas que cumplan esa condición sean actualizadas. Ejemplos:

Nota: Si el resultado es (0 row(s) affected), significa que no hay registros que cumplan la condición especificada en la cláusula WHERE.

```sql
UPDATE Articulos SET Nombre = 'Pala Ancha' WHERE Nombre = 'Pala';
```

```sql
UPDATE Articulos SET Precio = '499.99' WHERE Nombre = 'Pala';
```

```sql
UPDATE Articulos SET Precio = '499.99' WHERE Nombre <> 'Pala';
```

#### Desbloqueo de Bases de Datos

En ocasiones, el motor de base de datos MySQL Workbench bloquea las bases de datos para evitar actualizaciones o eliminaciones involuntarias. Si se necesita realizar una actualización (o eliminación) de registros de una base de datos bloqueada, es necesario desbloquearla ejecutando la siguiente instrucción:

```sql
SET SQL_SAFE_UPDATES = 0;
```
## Consulta de Datos Anexados: DML INSERT

Se pueden insertar datos en una tabla a partir de una sentencia SELECT. De este modo, podrás realizar una inserción masiva de datos desde una tabla hacia otra en una sola instrucción o sentencia.

```sql
INSERT INTO TablaDestino (Columna1, ..., ColumnaX)
SELECT (Columna1, ..., ColumnaX)
FROM TablaOrigen;
```

#### Sintaxis:

Nota: La tabla de destino (llamada TablaDestino en el ejemplo anterior) debe tener la misma estructura que la consulta SELECT; es decir, la misma cantidad de columnas y tipos de datos compatibles.

# Consulta de eliminación
### Eliminar Registros de una Tabla: DML DELETE

Para eliminar registros de una tabla, se utiliza la sentencia DELETE. Al hacerlo, se deberá especificar la condición que deben cumplir los registros de la tabla a eliminar.

En el siguiente ejemplo, se eliminarían de la tabla Productos todas aquellas filas donde el campo idProducto contenga el valor 1. Recuerda que si no se especifica ninguna condición a través de una cláusula WHERE, se eliminarán todos los registros de la tabla sin ninguna limitación.

```sql
DELETE FROM Productos WHERE idProducto = 1;
```

### TRUNCATE TABLE

La sentencia DELETE se puede utilizar para eliminar todos los registros de una tabla, pero tiene la desventaja de no ser tan eficiente, ya que no resetea los valores de los campos AUTO_INCREMENT, entre otras limitaciones.

Por este motivo, si se desea vaciar completamente la tabla, es recomendable utilizar la sentencia TRUNCATE TABLE. Esta elimina los registros en su totalidad y deja la tabla vacía, de manera menos costosa en términos de rendimiento para el servidor de base de datos.

Ejemplo:

```sql
TRUNCATE TABLE Productos;
```


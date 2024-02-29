# Modulo 3 
- Respaldo de base de datos
- Funciones integradas de texto
- Funiones integradas de fecha
- Funciones matematicas integradas
- Funciones de agregacion

## Backup con MySQL Workbench

Para generar un **backup** de una base de datos en MySQL Workbench, sigue estos pasos:

1. Ejecuta el comando `Server Data Export`.
2. En la pantalla que aparece, selecciona la base de datos y las tablas que deseas respaldar.
   - Por defecto, todas las tablas se seleccionan. Deselecciona las que no quieras incluir.
3. En `Export Options`, elige si deseas crear archivos separados por tabla o un archivo único para toda la base de datos.
   - Para un archivo único, selecciona la opción `Export to Self-Contained File`.
4. Especifica la ubicación y el nombre del archivo de respaldo usando el botón con los 3 puntos.
5. Inicia el proceso con el botón `Start Export`.

Este proceso te permite recuperar tu base de datos en caso de daño o pérdida.

## Restaurar un Backup en MySQL Workbench

Para restaurar una base de datos desde un backup en MySQL Workbench, sigue estos pasos:

1. Ejecuta el comando `Server Data Import`.
2. Selecciona la opción `Import from Self-Contained File` y busca el archivo de backup usando el botón con los 3 puntos.
3. Una vez seleccionado el archivo de respaldo, inicia el proceso de restauración con el botón `Start Import`.
4. Tras restaurar el backup, verifica la existencia de la base de datos en el navegador de objetos. Puede ser necesario actualizar el navegador para ver la base de datos restaurada.

Este proceso te permite recuperar tu base de datos a un estado anterior de manera eficiente.

## Funciones Integradas en MySQL

MySQL proporciona una variedad de funciones integradas para optimizar la manipulación y presentación de los datos. A continuación, se destacan algunas funciones de texto esenciales:

### CONCAT()
- Concatena varias cadenas de texto en una sola.
- Ejemplo: `SELECT CONCAT('Sr./a. ', NOMBRE, ' ', APELLIDO) as 'Nombre completo' FROM clientes;`

### CONCAT_WS()
- Similar a `CONCAT`, pero permite definir un separador.
- Ejemplo: `SELECT CONCAT_WS(',', nombre, apellido, cuit, direccion) as 'Datos Completos' FROM clientes;`

### UPPER() y LOWER()
- Convierte cadenas a mayúsculas o minúsculas, respectivamente.
- Ejemplos: 
  - `SELECT UPPER(nombre) Nombres FROM clientes;`
  - `SELECT LOWER(apellido) FROM clientes;`

### LEFT() y RIGHT()
- Extrae caracteres desde el inicio o el final de una cadena.
- Ejemplos: 
  - `SELECT LEFT(nombre, 1) As Inicial_nombre FROM clientes;`
  - `SELECT RIGHT(cuit, 1) as 'Dígito verificador' FROM clientes;`

### SUBSTRING()
- Extrae una subcadena especificando posición y longitud.
- Ejemplo: `SELECT SUBSTRING(cuit, 4, 8) as 'DNI' FROM clientes;`

### CHAR_LENGTH()
- Retorna la longitud de una cadena, incluyendo espacios.
- Ejemplo: `SELECT direccion, CHAR_LENGTH(direccion) as ‘Cantidad de caracteres’ FROM clientes;`

### LOCATE()
- Encuentra la posición de una subcadena dentro de otra.
- Ejemplo: `SELECT direccion, LOCATE('ara',direccion) 'Posición' from clientes;`

### LTRIM(), RTRIM() y TRIM()
- Eliminan espacios al inicio, al final, o ambos, de una cadena.
- Ejemplos: 
  - `SELECT LTRIM(direccion) Direccion_Correcta from clientes;`
  - `SELECT RTRIM(direccion) Direccion_Correcta from clientes;`
  - `SELECT TRIM(direccion) Direccion_Correcta from clientes;`

### REPLACE()
- Busca y reemplaza una cadena por otra dentro de un campo.
- Ejemplo: `SELECT REPLACE(direccion, 'Av.', 'Avenida') Direccion from clientes;`

Estas funciones son fundamentales para el manejo eficiente de datos en MySQL, permitiendo una amplia gama de operaciones de manipulación de texto directamente en las consultas SQL.


## Funciones de Fecha en MySQL

### Función `YEAR()`
- **Propósito:** Extrae el año de una fecha.
- **Ejemplo:** 
  - `SELECT YEAR(fecha) AS 'Año' FROM facturas;`


### Función `MONTH()`
- **Propósito:** Extrae el mes de una fecha.
- **Ejemplo:** 
  - `SELECT MONTH(fecha) AS 'Mes' FROM facturas;`

### Función `DAY()`
- **Propósito:** Extrae el día de una fecha.
- **Ejemplo:** 
  - `SELECT DAY(fecha) AS 'DIA' FROM facturas;`

### Función `HOUR()`
- **Propósito:** Extrae la hora de un timestamp.
- **Ejemplo:** 
  - `SELECT HOUR(fecha) AS 'HORA' FROM facturas;`

### Función `CURDATE()`
- **Propósito:** Devuelve la fecha actual del sistema.
- **Ejemplo:** 
  - `SELECT CURDATE() AS 'FECHA ACTUAL';`

### Función `CURTIME()`
- **Propósito:** Devuelve la hora actual del sistema.
- **Ejemplo:** 
  - `SELECT CURTIME() AS 'HORA ACTUAL';`
  
### Función `DATEDIFF()`
- **Propósito:** Calcula la diferencia en días entre dos fechas.
- **Ejemplo:** 
  - `SELECT DATEDIFF('2020-06-30', '2020-01-01') AS 'DIAS TRANSCURRIDOS';`

### Función `TIMESTAMPDIFF()`
- **Propósito:** Calcula la diferencia en una unidad específica (segundos, minutos, horas, días, meses, años) entre dos fechas.
- **Ejemplo:** 
  - `SELECT TIMESTAMPDIFF(MONTH, '2020-01-01', '2020-06-30') AS 'MESES TRANSCURRIDOS';`

### Función `DAYNAME()`
- **Propósito:** Devuelve el nombre del día de la semana de una fecha.
- **Ejemplo:** 
  - `SELECT DAYNAME(CURDATE()) AS 'Nombre del día';`

### Función `DAYOFWEEK()`
- **Propósito:** Devuelve el índice del día de la semana de una fecha (1 = Domingo, 2 = Lunes, ..., 7 = Sábado).
- **Ejemplo:** 
  - `SELECT DAYOFWEEK(CURDATE()) AS 'Número del día de la semana';`

### Función `DAYOFYEAR()`
- **Propósito:** Devuelve el número del día del año de una fecha.
- **Ejemplo:** 
  - `SELECT DAYOFYEAR(CURDATE()) AS 'Día del año';`

### Función `MONTHNAME()`
- **Propósito:** Devuelve el nombre del mes de una fecha.
- **Ejemplo:** 
  - `SELECT MONTHNAME(CURDATE()) AS 'Nombre del mes';`

### Función `ADDDATE()`
- **Propósito:** Añade un intervalo de tiempo especificado a una fecha.
- **Ejemplo:** 
  - `SELECT ADDDATE('2020-01-01', INTERVAL 1 MONTH) AS 'Fecha con un mes añadido';`

## Funciones Matemáticas Integradas en MySQL

MySQL ofrece varias funciones matemáticas integradas para realizar operaciones numéricas. A continuación, se presentan algunas de estas funciones junto con ejemplos de su uso:

### Función `ROUND()`

- **Propósito:** Redondea valores numéricos.
- **Ejemplo:** 
  - `SELECT ROUND(precio/3, 2) FROM articulos;`

### Función `CEIL()`

- **Propósito:** Devuelve el valor entero mayor al argumento especificado.
- **Ejemplo:** 
  - `SELECT precio, precio * 1.27 AS 'Precio con aumento', CEIL(precio * 1.27) AS 'Precio redondeado' FROM articulos;`

### Función `FLOOR()`

- **Propósito:** Devuelve el valor entero menor al argumento especificado.
- **Ejemplo:** 
  - `SELECT precio, precio * 1.27 AS 'Precio con aumento', FLOOR(precio * 1.27) AS 'Precio redondeado' FROM articulos;`

### Función `MOD()`

- **Propósito:** Obtiene el resto de la división de dos valores numéricos.
- **Ejemplo:** 
  - `SELECT MOD(15, 4);`

### Función `POW()`

- **Propósito:** Eleva un valor numérico a una potencia.
- **Ejemplo:** 
  - `SELECT POW(2, 8);`

Estos ejemplos te ayudarán a comprender cómo utilizar estas funciones matemáticas integradas en MySQL para realizar cálculos numéricos en tus consultas.

## Funciones de Agregado / Agrupamiento

En SQL existen funciones que nos permiten contar registros, calcular sumas, promedios, obtener valores máximos y mínimos. Estas funciones se denominan funciones de agregado porque operan sobre conjuntos de registros en lugar de hacerlo sobre datos individuales. A continuación, se presentan algunas de estas funciones:

### Función `COUNT()`

- **Propósito:** Retorna la cantidad de valores que contiene un campo especificado.
- PERMITE CONTAR REGISTROS
- **Ejemplo:** 
  - `SELECT COUNT(*) FROM Productos;`

### Función `SUM()`

- **Propósito:** Retorna la suma de los valores que contiene un campo especificado.
- PERMITE SUMAR LOS VALORES NUMERIOS DE UN CAMPO
- **Ejemplo:** 
  - `SELECT SUM(Stock) FROM Productos;`

### Función `MIN()`

- **Propósito:** Permite calcular el valor mínimo de un campo.
- **Ejemplo:** 
- PERMITE OBTENER EL VALOR MAS BAJO DE UN CONJUTNO DE VALORES NUMERICOS DE UN CAMPO
  - `SELECT MIN(Precio) FROM Productos;`

### Función `MAX()`

- **Propósito:** Permite averiguar el valor máximo de un campo.
- **Ejemplo:** 
- PERMITE OBTENER EL VALOR MAS ALTO DE UN CONJUTNO DE VALORES NUMERICOS DE UN CAMPO
  - `SELECT MAX(Precio) FROM Productos;`

### Función `AVG()`

- **Propósito:** Retorna el valor promedio de los valores del campo especificado.
- PERMITE PROMEDIAR LOS VALORES NUMERICOS DE UN CAMPO
- **Ejemplo:** 
  - `SELECT AVG(Precio) FROM Productos;`

## Cláusula `GROUP BY`

La cláusula `GROUP BY` se utiliza para agrupar información de acuerdo a un criterio en común. Por lo general, se utiliza con funciones de agregación. El comportamiento de `GROUP BY` dependerá de la función de agregación que se esté utilizando.
```SQL
SELECT Categoria, SUM(Stock) FROM Productos GROUP BY Categoria;
```

## Cláusula `HAVING`

La cláusula `HAVING` permite hacer selecciones (filtrar) en situaciones en las que no es posible usar la cláusula `WHERE`, dado que se establece un criterio sobre un valor dado por una función de agrupamiento y no por valores de registros.

Ejemplo:
```SQL
SELECT Categoria, SUM(Stock) FROM Productos GROUP BY Categoria HAVING SUM(Stock) > 250;
```










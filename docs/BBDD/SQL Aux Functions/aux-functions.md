---
title: Funciones Auxiliares
description: "Recopilatorio de algunas funciones especialmente útiles a la hora de construir consultas, principalmente funciones matemáticas y de cadenas."
---

- [LIMIT](#limit)
- [Matemáticas](#matemáticas)
  - [Redondeo de valores](#redondeo-de-valores)
  - [Máximos, mínimos, sumas y medias](#máximos-mínimos-sumas-y-medias)
  - [COUNT()](#count)
- [Cadenas](#cadenas)
  - [UPPER() y LOWER()](#upper-y-lower)
  - [CONCAT_WS()](#concat_ws)
  - [WILDCARDS (para búsqueda de cadenas)](#wildcards-para-búsqueda-de-cadenas)

## LIMIT

Devuelve las x primeras filas de una consulta:

``` sql
SELECT * FROM fabricante f LIMIT 5;
```

Devuelve dos filas empezando por la 3ºa, devuelve entonces las filas cuatro y tres:

`LIMIT <start><nº of columns>`

``` sql
SELECT * FROM fabricante f LIMIT 3,2;
```

## Matemáticas

### Redondeo de valores

| Comando      | Comportamiento                        |
| ------------ | ------------------------------------- |
| `ROUND()`    | Redondea de forma normal.             |
| `FLOOR()`    | Redondea hacia abajo siempre.         |
| `CEILING()`  | Redondea hacia arriba siempre.        |
| `TRUNCATE()` | Trunca hasta un nº dado de decimales. |

``` SQL
SELECT 
  p.nombre, 
  TRUNCATE( p.precio, 2 ) as "precio" 
FROM producto p;
```

### Máximos, mínimos, sumas y medias

Agrupan los resultados de la consulta en un único valor. Por esta razón se suelen usar junto con el comando **`GROUP BY`**.

| Comando | Comportamiento                       |
| ------- | ------------------------------------ |
| `MAX()` | Muestra la ocurrencia más alta.      |
| `MIN()` | Muestra la ocurrencia más baja.      |
| `SUM()` | Suma todas las ocurrencias.          |
| `AVG()` | Calcula la media de las ocurrencias. |

``` sql
SELECT 
  p.nombre as "nombre de producto", 
  p.precio as "euros", 
  ROUND( p.precio * 1.13, 2 ) as "dólares" 
FROM producto p;
```

### COUNT()

Cuenta el número de ocurrencias de aquello que esté entre paréntesis. Se suele usar para contar el número de filas que satisfacen algún criterio de búsqueda.

```sql
SELECT COUNT(p.precio) FROM producto p
WHERE p.precio > 50;
```

## Cadenas

### UPPER() y LOWER()

Transforman una string a uppercase o lowercase. Lo usamos principalmente para comparar strings sin preocuparnos por la capitalización de los datos.

``` sql
SELECT UPPER( p.nombre ), p.precio FROM producto p;
```

### CONCAT_WS()

Concatena una serie de datos separándolos con el separador
dado.

``` sql
SELECT 
  p.nombre AS "Nombre",
  CONCAT_WS(" ", ROUND(p.precio * 1.21), "€") AS "Precio" 
FROM producto p;
```

### WILDCARDS (para búsqueda de cadenas)

| Symbol | Explicación                                      | Ejemplo                                  |
| :----: | ------------------------------------------------ | ---------------------------------------- |
|  `%`   | Zero or more characters.                         | `bl%` finds bl, black, blue, and blob    |
|  `_`   | A single character.                              | `h_t` finds hot, hat, and hit            |
|  `[]`  | Any single character within the brackets.        | `h[oa]t` finds hot and hat, but not hit  |
|  `^`   | Any character not in the brackets.               | `h[^oa]t` finds hit, but not hot and hat |
|  `_`   | Any single character within the specified range. | `c[a-b]t` finds cat and cbt              |

Ejemplillos:

```sql
-- Devuelve todas las ciudades empezando por cualquier letra y acabando en "ondon".
SELECT * FROM Customers
WHERE City LIKE '_ondon';
```

```sql
-- Devuelve todas las ciudades que empiezan por "b", "s" o "p".
SELECT * FROM Customers
WHERE City LIKE '[bsp]%';
```

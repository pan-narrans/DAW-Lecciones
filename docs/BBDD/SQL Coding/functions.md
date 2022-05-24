---
title: Functions
description: "A function is a stored script returning a sole value. Their purpose is to encapsulate useful and commonly used pieces of code to be used inside procedures."
---

- [Calling a function](#calling-a-function)
- [Creating a function](#creating-a-function)
- [Example](#example)

{{ page.description }}

## Calling a function

To call a SQL function you need to put it inside a `SELECT` statement.

```sql
SELECT getIdLibro("Mort");
```

```sql
SELECT libro.titulo, libro.libro,
  getIdLibro(libro.titulo) 
  AS "Libro Calculado" FROM libro;
```

## Creating a function

You can do it from the mySQL interface or by coding.

```sql
CREATE FUNCTION <functionName> ([<parameter1>[,...]])
RETURNS datatype
```

If a functions doesn't receive any parameters, we leave the `()` blank.

## Example

> Ejemplo sacado del examen.

```sql
DROP FUNCTION IF EXISTS getCategory;

DELIMITER //

/*
Función que toma como parámetro una fecha y devuelve a que categoría pertenece. 

Esta  función debe calcular la edad con respecto a la fecha actual.

INFANTIL  → de 8 a 10 años
CADETE    → de 11 años a 14 años
JUVENIL   → de 15 a 17 años.
ADULTO    → mayores de 18 años.
*/

CREATE FUNCTION getCategory (fecha DATE)
RETURNs VARCHAR(20)
BEGIN

  DECLARE edad INT;
  DECLARE categoria VARCHAR(20);

  SET edad = TIMESTAMPDIFF(YEAR,fecha,NOW());

  IF edad >= 8 AND edad <= 10 THEN
    SET categoria = "INFANTIL";
  ELSEIF edad >= 11 AND edad <= 14 THEN
    SET categoria = "CADETE";
  ELSEIF edad >= 15 AND edad <= 17 THEN
    SET categoria = "JUVENIL";
  ELSEif edad >= 18 THEN
    SET categoria = "ADULTO";
  ELSE
    SET categoria = "ERROR";
  END IF;

  RETURN categoria;

END //

DELIMITER ;

-- TESTS

-- Muestra la categoría de todos los participantes
SELECT getCategory(fecha) FROM participante;
```

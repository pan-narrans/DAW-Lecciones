---
title: Procedures
description: "They allow us to create scripts for making complex queries and call them directly from the SQL console, saving us precious time ⏲
"
---

- [Parameters](#parameters)
- [Calling a procedure](#calling-a-procedure)
- [Creating a procedure](#creating-a-procedure)
- [Example](#example)

{{ page.description }}

While a function can call another function and a procedure can call a function, a procedure **cannot call** another procedure.

## Parameters

- **IN** :
  - Se pasa por valor.
- **OUT** :
  - Se pasa por copia, pero se asume que no lo inicializamos.
- **INOUT** :
  - Se pasa por copia (como el OUT), pero se asume que lo inicializamos.

## Calling a procedure

Unlike [functions](functions.md), procedures can be called directly from the SQL console but can't be called from another function or procedure.

```sql
CALL <procedureName>([parameter1[,...]])
```

## Creating a procedure

```sql
CREATE PROCEDURE <procedureName>([parameter1[,...]])
BEGIN
<routine_body>
END <DELIMITER>
```

## Example

Full script example ready to be copied and pasted. Note the comments explaining what the procedure is supposed to do.

> Ejemplo sacado de un examen

```sql
DROP PROCEDURE IF EXISTS inscribir;

DELIMITER //

/*
Recibe como parámetro de entrada el id de la competición e inserta en la tabla CompeticionParticipante todos los participantes de esa competición.

Por ejemplo:
CALL inscribir(9) dará como resultado la inserción en la tabla de CompeticionParticipante de todos los participantes de categoría Adulto, porque la competición 9 es de la categoria adultos.
*/

CREATE PROCEDURE inscribir (competicion_id INT)
BEGIN

DECLARE cat VARCHAR(20);

SELECT categoria INTO cat FROM competicion 
WHERE id = competicion_id;

INSERT INTO competicionparticipante
SELECT competicion_id, id, NOW() FROM participante
WHERE getCategory(fecha) = cat;

END //

DELIMITER ;
```

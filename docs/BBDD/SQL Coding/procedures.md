---
title: Procedures
description: "They allow us to create scripts for making complex queries and call them directly from the SQL console, saving us precious time ⏲
"
---

- [Parameters](#parameters)
- [Calling a procedure](#calling-a-procedure)
- [Creating a procedure](#creating-a-procedure)

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

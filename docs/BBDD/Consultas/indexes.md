---
title: Índices SQL
description: "Nos permiten agilizar la búsqueda de datos de las consultas a cambio de guardar un par más de datos para mantener el índice."
---

- [Crear un índice](#crear-un-índice)

{{ page.description }}

## Crear un índice

Tenemos dos opciones para crear índices en SQL:

- A la vez que cuando creamos la tabla.
- Después de crear la tabla

```sql
CREATE TABLE t(
   row1 INT PRIMARY KEY,
   row2 INT NOT NULL,
   row3 INT NOT NULL,
   INDEX (row2,row3) 
);
```

```sql
CREATE INDEX index_name ON table_name (column_list);
```

---
title: Crear y editar tablas
description: "Vamos a ver como crear tablas y editarlas una vez ya creadas sin tener que eliminarlas, manteniendo así los datos que ya puedan tener introducidos."
---

- [Crear una tabla nueva](#crear-una-tabla-nueva)
- [Alter](#alter)
  - [ADD](#add)
  - [DROP](#drop)
  - [MODIFY](#modify)

## Crear una tabla nueva

La sintaxis básica, como ya hemos visto, es esta:

```sql
CREATE TABLE table_name(
  column1 data_type(size),
  column2 data_type(size),
  ....
);
```

Dentro de esta sintaxis podemos añadir las `CONSTRAINTS` de clave primaria o clave foránea que nos permiten identificar registros y relacionar distintas tablas entre sí, respectivamente. Pero esto lo vamos a ver en otra página.

## Alter

En el caso de que necesitemos editar una tabla y que crearla desde zero no sea una opción viable, podemos hacer un `ALTER`. El comando ALTER nos ofrece tres (3) viene en tres sabores:

### ADD

Para añadir nuevas columnas o constraints a una tabla ya existente.

```sql
-- Añadir una columna
ALTER TABLE table_name
ADD column_name data_type;
```

```sql
-- Añadir una constraint
ALTER TABLE table_name
ADD CONSTRAINT constraint_name PRIMARY KEY (column_name[,...]);
```

### DROP

Para eliminar columnas o constraints de una tabla ya existente:

```sql
-- Eliminar una columna
ALTER TABLE table_name
DROP COLUMN column_name;
```

```sql
-- Eliminar una constraint
ALTER TABLE table_name
DROP CONSTRAINT constraint_name;
```

### MODIFY

Para cambiar el tipo de dato de una columna:

```sql
ALTER TABLE table_name
MODIFY column_name data_type;
```

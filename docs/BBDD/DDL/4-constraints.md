---
title: Constraints **WIP**
description: "Crear constraints de clave primaria o foránea desde zero y como editarlas o borrarlas en caso de error."
---

Dentro de esta sintaxis podemos añadir las `CONSTRAINTS` de clave primaria o clave foránea.

### Clave Primaria

Las claves primarias se definen automáticamente como `UNIQUE`y permiten identificar de forma inequívoca un registro de una tabla. Es muy común que sean de tipo `INT` pero pueden ser de otros tipos. Tenemos varias formas de crearlas.

La más común es declarando la clave en la misma línea que la columna. Esto únicamente es válido para **claves primarias simples**.

```sql
CREATE TABLE table_name(
  column1 data_type PRIMARY KEY,
  ....
);
```

Otra opción es declarar la clave después de las columnas.

```sql
CREATE TABLE table_name(
  column1 data_type,
  ....
  PRIMARY KEY (column1)
);
```

Declarando la clave al final podemos también declarar **claves primarias compuestas**:

```sql
CREATE TABLE table_name(
  column1 data_type,
  column2 data_type,
  ....
  PRIMARY KEY (column1, column2)
);
```

### Claves Foráneas

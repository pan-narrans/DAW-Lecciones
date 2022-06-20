---
title: Comandos Básicos
description: "`CREATE`, `DROP`, `ALTER`, `TRUNCATE`"
---

- [CREATE](#create)
- [DROP](#drop)
- [ALTER](#alter)
- [TRUNCATE](#truncate)

Vamos a usar estos comandos para tratar con:

- bases de datos
- tablas
- vistas
- procedimientos
- funciones

Los comandos `CREATE` y `DROP` son comunes a todas las estructuras.

Los comandos `ALTER` y `TRUNCATE` son específicos para tablas.

## CREATE

Usado para crear las estructuras ~~duh~~.

```sql
CREATE TABLE table_name(
  column1 data_type(size),
  column2 data_type(size),
  ....
);
```

```sql
CREATE DATABASE database_name;
```

## DROP

Usado para eliminar una estructura. Se suele combinar con `IF EXISTS` para evitar generar un error en caso de intentar eliminar una estructura que no exista.

```sql
DROP DATABASE IF EXISTS database_name;
```

## ALTER

Usado para modificar una tabla ya existente.

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

## TRUNCATE

Elimina todos los registros de una tabla sin disparar ningún trigger. Es equivalente a hacer un `DROP` seguido de un `CREATE`, pero mucho más rápido.

Se considera DDL y no DML (aunque esté afectando a los datos) ya que **no puede hacerse un rollback** (deshacer la operación) y se necesitan permisos de ALTER para poder ejecutarlo, no de WRITE.

```sql
TRUNCATE TABLE table_name;
```

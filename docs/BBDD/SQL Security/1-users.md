---
title: Gestión de usuarios
description: "Ejemplos de como gestionar usuarios y sus privilegios."
---

{{ page.description }}

- [Usuarios](#usuarios)
  - [Crear usuarios](#crear-usuarios)
  - [Conectarse a la base de datos](#conectarse-a-la-base-de-datos)
- [Privilegios](#privilegios)
  - [Dar privilegios](#dar-privilegios)
  - [Eliminar privilegios](#eliminar-privilegios)
  - [Mostrar privilegios](#mostrar-privilegios)

## Usuarios

### Crear usuarios

El nombre de la cuenta se compone del nombre de usuario y el nombre del host a través del cual nos conectamos a la base de datos. En nuestro caso el host es `localhost` ya que trabajamos en un servidor local.

```sql
CREATE USER [IF NOT EXISTS] username@hostname 
IDENTIFIED BY 'password';
```

### Conectarse a la base de datos

```sql
mysql -u username -p
```

```sql
Enter password: ********
```

## Privilegios

Estos son los privilegios que podemos conceder:

- `SELECT`
- `UPDATE`
- `INSERT`
- `ALL`: todos los privilegios

Los privilegios se pueden conceder a distintos niveles:

![gráfico con los distintos niveles de privilegios](../img/MySQL-Grant-Privilege-Level.png)

<figcaption> Imagen de <a>mysqltutorial.org</a>. </figcaption>

- **Globales**:
  - Afectan a todas las bases de datos dentro de un servidor MySQL.
  - `ON *.*`
- **Base de datos**:
  - Afectan a la totalidad de objetos que se encuentren en una base de datos dada.
  - `ON <database_name>.*`
- **Tabla**:
  - Afecta a todas las columnas de una tabla.
  - `ON <database_name>.<table_name>`
  - En el caso de no incluir el nombre de la base de datos MySQL usará la base de datos por defecto.
- **Columna**:
  - Afecta a una única columna dentro de una tabla.
  - Tiene que indicarse el nombre de la columna para cada permiso que se quiera conceder.
    - `SELECT (<column_name>, ...)`
  - `ON <database_name>.<table_name>`
- Rutina:
  - Permite la ejecución de la rutina.
  - `ON PROCEDURE <procedure_name>`
- Proxy:
  - Permite hacer de un usuario una "copia" de otro, dándole todos sus permisos.

### Dar privilegios

Sintaxis:

```sql
GRANT privilege [,privilege],.. 
ON privilege_level 
TO account_name;
```

Ejemplos:

```sql
-- Otorga a bob privilegios de SELECT en la tabla 'employees'.
GRANT SELECT
ON employees
TO bob@localhost;
```

```sql
-- Otorga a super todos los privilegios en la totalidad de la base de datos
-- 'classicmodels'.
GRANT ALL 
ON classicmodels.* 
TO super@localhost;
```

### Eliminar privilegios

```sql
REVOKE privilegee [,privilege]..
ON [object_type] privilege_level
FROM user1 [, user2] ..;
```

### Mostrar privilegios

```sql
SHOW GRANTS FOR super@localhost;
```

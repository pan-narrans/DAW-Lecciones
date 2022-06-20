---
title: Vistas en MySQL
description: "Las vistas permiten limitar y controlar el acceso a los datos haciendo un corta y pega de las cosas que queremos que vea el cliente."
---

- [Crear una vista](#crear-una-vista)
- [Consultar una vista](#consultar-una-vista)
- [Eliminar una vista](#eliminar-una-vista)

{{ page.description }}

Son *fotos* de partes de la base de datos, por lo que tienen la ventaja de estar "descolgadas" de la tabla original (son copias de los datos) por lo que bloquean por completo el acceso a la tabla original.

> Las vistas nos permiten guardar consultas para hacer referencia a ellas luego.

## Crear una vista

No tenemos más que ejecutar el comando `CREATE VIEW <name> AS` seguido de la consulta que queremos guardar como vista.

```sql
CREATE VIEW customerPayments AS 
SELECT 
    customerName, 
    checkNumber, 
    paymentDate, 
    amount
FROM
    customers
INNER JOIN
    payments USING (customerNumber);
```

## Consultar una vista

A efectos de consulta, una vista se comporta de la misma manera que una tabla. Por lo que podemos obtener sus datos con un simple `SELECT`.

```sql
SELECT * FROM customerPayments;
```

## Eliminar una vista

Como todo en esta vida, las vistas se eliminan con el comando `DROP`.

```sql
DROP VIEW IF EXISTS customerPayments;
```

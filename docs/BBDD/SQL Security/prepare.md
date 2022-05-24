---
title: Preparación de consultas
description: "
Por temas de seguridad y de rendimiento, tenemos la opción de dejar preparada de antemano una consulta, para luego rellenarla con los datos necesarios.


Esto es especialmente útil en consultas que se vayan a ejecutar varias veces seguidas, esto le ahorra al compilador de SQL el parsear mil veces la misma consulta.


Aparte, nos permite evitar varios casos de inyección SQL.
"
---
- [Sintaxis del predicado](#sintaxis-del-predicado)
- [Proceso a seguir](#proceso-a-seguir)

{{ page.description }}

> Podemos preparar consultas *(SQL dinámico)* dentro de procedimientos y a pelo en la consola de SQL que nos proporciona phpMyAdmin. **No** se pueden usar consultas preparadas en disparadores o funciones.

## Sintaxis del predicado

```sql
SELECT * FROM products 
WHERE productCode = ?;
```

Los `?` son los huecos que dejamos libres para luego realizar la llamada.

## Proceso a seguir

- `PREPARE`: preparamos la consulta.
- `EXECUTE`: la ejecutamos cuantas veces necesitemos.
- `DEALLOCATE PREPARE`: liberamos la consulta.

![diagrama de los pasos a seguir](../img/MySQL-Prepared-Statement.png)

<figcaption> Imagen de <a>mysqltutorial.org</a>. </figcaption>

Preparamos la consulta:

```sql
PREPARE statement1 FROM 
  'SELECT productCode, productName 
   FROM products WHERE productCode = ?';
```

Realizamos la consulta:

```sql
SET @pc = 'S10_1678'; 
EXECUTE statement1 USING @pc;
```

Liberamos la consulta preparada:

```sql
DEALLOCATE PREPARE statement1;
```

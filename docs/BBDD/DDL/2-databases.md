---
title: Crear una base de datos
description: "Comandos para crear una nueva base de datos o para sustituir una ya existente. Es importante porque si no tenemos bases de datos no podemos hacer nada más."
---

El siguiente grupo de comandos es el que más vamos a usar a la hora de hacer ejercicios o pruebas:

```sql
DROP DATABASE IF EXISTS database_name;
CREATE database_name;
USE database_name;
```

- eliminar la base de datos en caso de que ya exista (evita errores)
- crear la base de datos
- indicarle al servidor que queremos usar la base de datos (para comandos posteriores)

**IMPORTANTE:** Lógicamente, al hacer un `DROP` estamos eliminando la base de datos ya existente y únicamente lo vamos a hacer cuando queramos empezar de nuevo un ejercicio o tengamos todo guardado en archivos. Si tenemos cosas que no queremos perder o no podemos recuperar dentro de la base de datos, nos va a tocar hacer una nueva con un nombre que no exista.

Si únicamente queremos crear la base de datos vamos a usar:

```sql
CREATE database_name;
USE database_name;
```

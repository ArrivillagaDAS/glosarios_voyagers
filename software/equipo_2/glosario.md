### Índice (Index)

**Descripción:**
Esto de los índices en PostgreSQL me costó entenderlo al principio pero al final es más simple de lo que suena. Básicamente cuando uno tiene una tabla con muchísimos datos y hace una consulta, por defecto la base de datos revisa fila por fila hasta encontrar lo que se le pidió, y si la tabla es grande eso puede tardar bastante. Un índice lo que hace es dejar como un "atajo" guardado sobre cierta columna para que cuando se busque algo por ahí, no tenga que revisar todo sino que llegue casi directo al dato.

Es parecido a cuando uno busca una palabra en el diccionario: no vas leyendo página por página desde el principio, sino que te guías por el orden alfabético para llegar rápido. Ahora, algo que hay que tener cuidado es que ponerle índice a todo tampoco es buena idea, porque cada índice ocupa espacio y además cuando uno inserta o actualiza datos, ese índice también se tiene que actualizar, entonces si se abusa de los índices las escrituras se vuelven más lentas. Lo normal es ponerle índice solo a las columnas que uno sabe que va a usar seguido en los `WHERE` o para ordenar resultados.

**Ejemplo (si aplica):**
Digamos que en la tabla de usuarios uno busca constantemente por correo para hacer login, entonces tendría sentido hacer esto:

```sql
CREATE INDEX idx_usuarios_correo ON usuarios (correo);
```

Y ya después, cuando se corre algo como `SELECT * FROM usuarios WHERE correo = 'ejemplo@correo.com';`, la búsqueda va a ser mucho más rápida que si no existiera ese índice, sobre todo entre más crezca la tabla.

### Transacción

**Descripción:**
Una transacción, tal como yo la entiendo, es cuando uno agrupa varias operaciones (inserts, updates, lo que sea) y las trata como si fueran una sola cosa, no varias por separado. La idea de fondo es que, o se hacen todos los cambios juntos, o no se hace ninguno, para que la base de datos nunca quede a la mitad de algo.

Esto tiene sentido sobre todo cuando una operación depende de otra. Por ejemplo, si uno tiene que restarle dinero a una cuenta y sumárselo a otra, esas dos cosas tienen que pasar juntas necesariamente, porque si por alguna razón se corta a la mitad (se cae la conexión, hay un error, lo que sea) y solo se aplicó la resta pero no la suma, ahí sí que hay un problema serio: el dinero desapareció de un lado y nunca llegó al otro. Para evitar justo eso existen las transacciones: uno empieza con `BEGIN`, hace los cambios que necesite, y al final decide si los confirma con `COMMIT` o si los deshace todos con `ROLLBACK` como si nunca hubiera pasado nada.

**Ejemplo (si aplica):**
El ejemplo clásico es justo el de transferir dinero entre cuentas:

```sql
BEGIN;
UPDATE cuentas SET saldo = saldo - 100 WHERE id = 1;
UPDATE cuentas SET saldo = saldo + 100 WHERE id = 2;
COMMIT;
```

Si algo sale mal después del primer `UPDATE` y antes del `COMMIT`, en vez de confirmar se hace `ROLLBACK`, y ya con eso ninguno de los dos cambios queda guardado. Así uno se asegura de que nunca vaya a quedar dinero "flotando" de un lado sin haber llegado al otro.


### ARRAYS (PostgreSQL)

**Descripción:**
El tipo de dato **array** sirve para guardar varios datos juntos en un mismo lugar. La cantidad de datos que puede contener puede variar, y todos los datos que se guarden deben ser del mismo tipo.

Los arrays son útiles cuando necesitamos almacenar varios valores que pertenecen a una misma información.

**Ejemplo:**  
Si necesitamos guardar los números telefónicos de una persona y esta tiene dos números, en lugar de crear un espacio diferente para cada número, podemos utilizar un **array** para guardar los dos números juntos.

```postgresql
    CREATE TABLE personas (             
    id SERIAL PRIMARY KEY,              
    nombre VARCHAR(100),                 
    telefonos TEXT[]                     -- ARRAY: permite guardar varios teléfonos
);
```
Los corchetes [] indican que es un array, es decir, que podemos guardar varios valores en esa misma columna.

```postgresql
    INSERT INTO personas (nombre, telefonos)
    VALUES ('Carlos', ARRAY['55512345', '55567890']);
```
En este caso, Carlos tiene dos números de teléfono, y ambos se guardan dentro de la columna telefonos

### Comando COPY (PostgreSQL)

El comando **COPY** se utiliza para **cargar varios datos a una tabla de PostgreSQL de una sola vez**, normalmente desde un archivo.

```postgresql
  COPY personas(nombre, telefonos)       -- Indicamos la tabla y las columnas
  FROM '/ruta/personas.csv'              -- Indicamos el archivo que contiene los datos
  DELIMITER ','                          -- Indicamos que los datos están separados por comas
  CSV HEADER;                            -- Indicamos que el archivo está en formato CSV y tiene encabezados
```

Con el comando `COPY`, PostgreSQL puede tomar estos datos del archivo y guardarlos en la tabla **personas** de una sola vez
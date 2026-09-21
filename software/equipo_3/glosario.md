# Glosario Software

### 1. Node.js

- **Término:** Node.js  
- **Descripción:** Entorno de ejecución de código JavaScript que funciona fuera del navegador. Permite desarrollar aplicaciones del lado del servidor, APIs, herramientas de línea de comandos y aplicaciones web. Es multiplataforma y se utiliza junto con herramientas como npm para administrar paquetes.
- **Ejemplo:** Crear un servidor web sencillo con Node.js:

```javascript
const http = require("http");

const servidor = http.createServer((solicitud, respuesta) => {
  respuesta.writeHead(200, { "Content-Type": "text/plain" });
  respuesta.end("Hola desde Node.js");
});

servidor.listen(3000, () => {
  console.log("Servidor ejecutándose en el puerto 3000");
});
```

### 2. NVM

- **Término:** NVM — *Node Version Manager*  
- **Descripción:** Herramienta de línea de comandos que permite instalar, administrar y cambiar entre diferentes versiones de Node.js en un mismo equipo. Es útil cuando distintos proyectos requieren versiones específicas de Node.js.
- **Ejemplo:** Instalar y utilizar una versión determinada de Node.js:

```bash
nvm install 20
nvm use 20
node --version
```

`nvm install 20` instala Node.js versión 20, mientras que `nvm use 20` la activa para trabajar en el proyecto.


### 3. Asíncrono

* **Término:** Asíncrono — *Asynchronous*
* **Descripción:** Forma de ejecutar operaciones en programación que permite iniciar una tarea sin tener que esperar a que termine para continuar con otras instrucciones. Es especialmente útil para operaciones que pueden tardar, como consultas a bases de datos, solicitudes a APIs, lectura de archivos o comunicación con servidores.
* **Ejemplo:** Realizar una operación asíncrona en JavaScript utilizando `async` y `await`:

```javascript
async function obtenerDatos() {
    const respuesta = await fetch("https://api.ejemplo.com/datos");
    const datos = await respuesta.json();

    console.log(datos);
}

obtenerDatos();
```

En este ejemplo, `await` espera el resultado de la solicitud mientras JavaScript puede gestionar otras operaciones de forma asíncrona.

---

### 4. Cardinalidad

* **Término:** Cardinalidad — *Cardinality*
* **Descripción:** Concepto utilizado en bases de datos para indicar cuántos registros de una entidad pueden estar relacionados con los registros de otra entidad. Las relaciones más comunes son uno a uno (1:1), uno a muchos (1:N) y muchos a muchos (N:M).
* **Ejemplo:** Representar una relación entre clientes y pedidos:

```sql
CREATE TABLE clientes (
    id_cliente INT PRIMARY KEY,
    nombre VARCHAR(100)
);

CREATE TABLE pedidos (
    id_pedido INT PRIMARY KEY,
    id_cliente INT,
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente)
);
```

En este ejemplo, un cliente puede tener muchos pedidos, mientras que cada pedido pertenece a un solo cliente. Por lo tanto, la relación tiene una cardinalidad **uno a muchos (1:N)**.


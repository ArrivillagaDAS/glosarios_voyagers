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

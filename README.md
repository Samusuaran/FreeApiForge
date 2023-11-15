# ApiJsonServerGltich

## **Pasos del Tutorial:**

### Paso 1: Crear Archivos en Visual Studio Code.

1. Abre Visual Studio Code.

2. Crea un nuevo directorio para tu proyecto.

3. Dentro del directorio, crea los siguientes archivos:

   - `db.json` (para tus datos)
   - `package.json` (para las dependencias y scripts)
   - `server.js` (para la configuración del servidor)

## **Paso 2: Configurar `db.json` con Datos Iniciales.**

```
{
  "personajes": [
    { "id": 1, "nombre": "Personaje1", "tipo": "Atacante", "imagen": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIA..." },
    { "id": 2, "nombre": "Personaje2", "tipo": "Defensor", "imagen": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIA..." }
  ],
  "armas": [
    { "id": 1, "nombre": "Arma1", "tipo": "Rifle", "imagen": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIA..." },
    { "id": 2, "nombre": "Arma2", "tipo": "Pistola", "imagen": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIA..." }
  ],
  "mapas": [
    { "id": 1, "nombre": "Mapa1", "tipo": "Asalto", "imagen": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIA..." },
    { "id": 2, "nombre": "Mapa2", "tipo": "Control", "imagen": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIA..." }
  ]
}
```

## **Paso 3: Configurar `package.json`.**

```
{
  "name": "json-server-glitch-tutorial",
  "version": "1.0.0",
  "description": "Tutorial de JSON Server en Glitch",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "json-server": "^0.17.0"
  }
}
```

## **Paso 4: Configurar `server.js`**

```
const jsonServer = require('json-server');
const server = jsonServer.create();
const router = jsonServer.router('db.json');
const middlewares = jsonServer.defaults();

const PORT = process.env.PORT || 3000;

server.use(middlewares);
server.use(router);

server.listen(PORT, () => {
  console.log(`JSON Server is running on port ${PORT}`);
});
```

## **Paso 5: Inicializar Repositorio y Hacer Commit en GitHub.**


1. Inicializa un nuevo repositorio en GitHub.

2. Abre la terminal de Visual Studio Code.

3. Ejecuta los siguientes comandos:

   - git init
   - git add .
   - git commit -m "Inicializar proyecto con JSON Server"
   - git remote add origin https://github.com/tu-usuario/tu-repositorio.git
   - git push -u origin master
   

## **Paso 6: Vincular a Glitch.**

1. Ve a [Glitch](https://glitch.com/).

2. Crea un nuevo proyecto y selecciona "Importar desde GitHub".

3. Ingresa la URL de tu repositorio y sigue las instrucciones para importar.

¡Y eso es todo! Ahora tienes tu propia API en Glitch utilizando JSON Server. Puedes realizar solicitudes a las rutas específicas para obtener o modificar datos. ¡Diviértete explorando y personalizando tu API!.

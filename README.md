![Logo]( https://github.com/djsq200599/FreeApiForge/blob/main/FreeApiForgeLogo.png )

<p align="center">
  ¡Forja tu API con maestría, esculpe su grandeza en la red!
</p>

## Tabla de Contenidos
- [Implementación en Glitch](#implementación-en-glitch)
- [Implementación en AWS](#implementación-en-aws)
  
# Implementación en Glitch

## **Pasos para Implementar directamente a Glitch desde este repositorio.**

1. Regístrese en [Glitch](https://glitch.com/).
   
2. Haga clic en New project.
   
3. Haga clic en Import from GitHub.
   
4. Pegue https://github.com/djsq200599/ApiJsonServerGltich.git en la entrada del URL y haga clic en Aceptar.
   
5. Espere a que se configure.
   
6. Presione el botón Share para obtener su URL del sitio activo. Debería ser algo como por ejemplo: https://api-json-server.glitch.me. Y tu base de datos estará en https://api-json-server.glitch.me/posts.
   

## **Pasos para crear tu propio proyecto subirlo a tu repositorio de GitHub e implementar a Glitch:**

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


1. Inicializa un nuevo repositorio en [GitHub](https://github.com/).

2. Abre la terminal de Visual Studio Code.

3. Ejecuta los siguientes comandos:

   - git init
   - git add .
   - git commit -m "Inicializar proyecto con JSON Server"
   - git remote add origin https://github.com/tu-usuario/tu-repositorio.git
   - git push -u origin master
   

## **Paso 6: Vincular a Glitch.**

1. Ve a [Glitch](https://glitch.com/).

2. Crea un New project y selecciona "Import from GitHub".

3. Ingresa la URL de tu repositorio y sigue las instrucciones para importar.

¡Y eso es todo! Ahora tienes tu propia API en Glitch utilizando JSON Server. Puedes realizar solicitudes a las rutas específicas para obtener o modificar datos. ¡Diviértete explorando y personalizando tu API!.

# Implementación en AWS

# Configuración de un servidor JSON en AWS

## Paso 1: Configurar una instancia en AWS

1. Inicia sesión en tu cuenta de AWS.
2. Navega a la sección de EC2 (Elastic Compute Cloud).
3. Haz clic en "Launch Instance" para crear una nueva instancia.
4. Selecciona una imagen de máquina (AMI) basada en la distribución de Linux que prefieras.
5. Elige el tipo de instancia y configura los detalles según tus necesidades.
6. Configura la seguridad del grupo: Asegúrate de permitir el tráfico en el puerto que utilizarás para tu servidor JSON (por defecto, podría ser el puerto 80 o 8080 para HTTP).
7. Lanza la instancia y crea o selecciona una clave de acceso para conectarte a la instancia.

## Paso 2: Configurar el servidor JSON

1. Conéctate a tu instancia usando SSH y la clave de acceso que configuraste.

## Paso 3: Crea una carpeta para tu proyecto y navega hasta ella

1. Actualiza los paquetes del sistema ejecutando `sudo apt update && sudo apt upgrade`.
2. Instala Node.js: `sudo apt-get install nodejs`.
3. Instala NPM: `sudo apt install npm`.
4. Instala JSON Server: `npm install json-server`.

## Paso 4: Preparar tus datos

1. Crea un archivo JSON con tus datos. Puedes llamarlo, por ejemplo, db.json.
2. Agrega los datos que deseas exponer a través de la API en este archivo.

## Paso 5: Iniciar el servidor JSON

1. Crea un archivo llamado server.js.
2. En server.js, configura el servidor JSON utilizando el módulo json-server. Aquí tienes un ejemplo básico:

```
javascript
const jsonServer = require('json-server');
const server = jsonServer.create();
const router = jsonServer.router('/home/ubuntu/json-server/db.json');
const middlewares = jsonServer.defaults();

server.use(middlewares);
server.use(router);

const PORT = 8080; // Cambia esto al puerto que estés utilizando

server.listen(PORT, () => {
  console.log(`JSON Server is running on port ${PORT}`);
});

```

## Paso 6: Ejecuta el servidor JSON: node server.js.
Ahora deberías tener tu servidor JSON ejecutándose en la instancia de AWS en el puerto que hayas especificado. Puedes acceder a tus datos a través de la dirección IP pública de la instancia y el puerto que configuraste en el archivo server.js.

## Paso 7 (opcional): Inicio automático del server.js al iniciar nuevamente la instancia

1. Crear un archivo de servicio systemd para tu aplicación: crea un archivo de servicio en la ubicación /etc/systemd/system con un nombre descriptivo, por ejemplo json-server.service. Puedes usar un editor de texto como nano para crear y editar el archivo: sudo nano /etc/systemd/system/json-server.service.
3. Agrega el contenido del archivo de servicio:
```
[Unit]
Description=JSON Server
After=network.target

[Service]
ExecStart=/usr/bin/node /home/ubuntu/json-server/server.js
WorkingDirectory=/home/ubuntu/json-server
Restart=always
User=ubuntu

[Install]
WantedBy=multi-user.target
```
5. Asegúrate de que la ruta en ExecStart y WorkingDirectory sea correcta.

6. Recarga el sistema de systemd: Ejecuta el siguiente comando para recargar los archivos de configuración del sistema de systemd: sudo systemctl daemon-reload.

7. Inicia y habilita el servicio: Ejecuta los siguientes comandos para iniciar y habilitar el servicio para que se inicie automáticamente al arrancar: sudo systemctl start json-server y sudo systemctl enable json-server.

8. Verifica el estado del servicio: Verifica el estado del servicio para asegurarte de que se está ejecutando correctamente: sudo systemctl status json-server.

## Paso 8: Depuración de errores
Si estás experimentando dificultades para identificar el problema, puedes ejecutar manualmente el comando para iniciar tu servidor JSON en la terminal y observar cualquier mensaje de error que se imprima. Por ejemplo:

/usr/bin/node /home/ubuntu/json-server/server.js

Verifica los registros: Si el servicio no se inicia correctamente, revisa los registros detallados del servicio para obtener información adicional sobre el error:

journalctl -u json-server.service

¡Y eso es todo! Ahora tienes tu propia API en una instancia virtual de AWS utilizando JSON Server. Puedes realizar solicitudes a las rutas específicas para obtener o modificar datos. ¡Diviértete explorando y personalizando tu API!.

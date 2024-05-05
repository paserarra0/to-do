# TO DO LIST

To do es una aplicación en la que se visualiza una lista de tareas que podemos añadir o borrar. Forma parte del tuturial de inicio de Docker para aprender a usar contenedores e imágenes.
## Implementación y ejecución
Para la implementación de to-do, seguiremos los pasos del [tutorial docker](https://docs.docker.com/get-started/).
* Prequisitos
  * Instalación de Docker Desktop
  * Instalación de Git Client
  * Tener un IDE o editor de texto
* Clonar el repositorio getting-started
  ```
  git clone https://github.com/docker/getting-started-app.git
  ```
* Creamos Dockerfile en el directorio de getting-started y añadimos el siguiente texto
  ```
  # syntax=docker/dockerfile:1
  FROM node:18-alpine
  WORKDIR /app
  COPY . .
  RUN yarn install --production
  CMD ["node", "src/index.js"]
  EXPOSE 3000
  ```
* Construimos la imagen
  ```
  docker build -t getting-started .
  ```
* Iniciar la aplicación
  ```
  docker run -dp 127.0.0.1:3000:3000 getting-started
  ```

## Implemetación S-SDLC
Para el desarrollo de la aplicación se usará el marco de trabajo SDLC seguro para lograr un software seguro y robusto.
1. Nos aseguramos de descargar la última versión de las aplicaciones y comprobamos la veracidad de las fuentes (Docker Desktop, repositorio getting-started, etc...).
2. Identificación de los requisitos de autenticación y autorización. Establecemos usuarios y contraseñas para cada uno de los miembros involucrados en el proyecto y gestionamos sus privilegios.
3. Preparar una estrategia de alto nivel de recuperación de desastres y continuidad. En nuestro caso desarrollaremos la práctica en una máquina virtual. Crearemos copias de la máquina usada para asegurar que no se pierde nada importante en caso de que ocurra algún desastre.

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

# Zed Attack Proxy (ZAP)
Zed Attack Proxy (ZAP) es un escaner de aplicaciones web de código abierto. Para la instalación de esta aplicación nos dirigiremos a el siguiente link:
* [zaproxy.org](https://www.zaproxy.org/)
![zap1](https://github.com/paserarra0/to-do/assets/156304388/635adec0-cc48-4cd4-a6a7-9f590912df12)
A continuación seleccionaremos el isntalador de Linux ya que usaremos una máquina virtual Ubuntu 22.04
![zap2](https://github.com/paserarra0/to-do/assets/156304388/70ea8b39-7a15-4797-8831-f624ca47d297)
Una vez descargado el instalador, tendremos que instalar java si no lo tenemos descargado. Lo podremos hacer con los siguientes comandos:
```
  sudo apt install default-jre
  sudo apt install default-jdk
```
Para ejecutar el instalador tendremos que cambiar los permisos de la aplicación con el siguiente comando:
```
  chmod o+x ZAP_2_15_0_unix.sh
```
Finalmente lanzaremos el instalador con:
```
  sudo ./ZAP_2_15_0_unix.sh
```
A continuación se lanzará la interfaz gráfica del isntalador, solo tendremos que darle a "Next" hasta que finalice. Cuando termine la instalación se abrirá ZAP y veremos el menú principal.
![zap3](https://github.com/paserarra0/to-do/assets/156304388/383d98e9-4a74-48b1-bbc2-3d0a73d0f4eb)
![zap4](https://github.com/paserarra0/to-do/assets/156304388/bc8fec33-b1f9-4928-8533-ff45c713bc88)
Para lanzar un análisis automático le daremos al icono que se señala y completaremos el campo de URL con la dirección de la aplicación to-do.
![zap5](https://github.com/paserarra0/to-do/assets/156304388/7f4cda68-9dab-4a92-86c3-f45a44097a6d)
![zap6](https://github.com/paserarra0/to-do/assets/156304388/ed757189-8553-483f-be27-def7b79b75e2)
Podremos ver las alertas encontradas con sus respectivas alertas con sus respectivos detalles.
![zap7](https://github.com/paserarra0/to-do/assets/156304388/9353338f-e20a-47b2-91c2-52f5ffe7d682)

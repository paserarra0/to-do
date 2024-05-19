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
![zap1.png]()
A continuación seleccionaremos el isntalador de Linux ya que usaremos una máquina virtual Ubuntu 22.04
![zap2.png]()
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
![zap3.png]()
![zap4.png]()
Para lanzar un análisis automático le daremos al icono que se señala y completaremos el campo de URL con la dirección de la aplicación to-do.
![zap5.png]()
![zap6.png]()
Podremos ver las alertas encontradas con sus respectivas alertas con sus respectivos detalles.
![zap7.png]()

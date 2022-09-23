# Uso de contenedor Docker con Nginx

  ![WSL](https://docs.microsoft.com/sv-se/windows/images/windows-linux-dev-env.png)


## Tutorial hecho con [WSL](https://learn.microsoft.com/en-us/windows/wsl/install )(Windows Subsystem for Linux). 
### <br>También se puede realizar en máquinas virtuales como Virtual Box, Kali, etc.


 ## :one: Tener WSL al día
 
```
 sudo apt update
```
```
 sudo apt upgrade
```

## :two: Descarga del contenedor

![Docker](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Docker_%28container_engine%29_logo.svg/220px-Docker_%28container_engine%29_logo.svg.png)


En el entorno WSL descargamos [Docker](https://docs.docker.com/engine/install/ubuntu/)

Yo trabajé con Ubuntu, pero hay otras alternativas también.<br>


##   :large_blue_circle: Instalación usando el repositorio
 Configuración del repositorio -> Actualizamos el índice de paquetes apt e instalamos paquetes para permitir que apt use un repositorio a través de HTTPS:
```
sudo apt-get update
```

```
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
Agregamos la clave GPG oficial de Docker:
```
 sudo mkdir -p /etc/apt/keyrings
```
 
```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
 Usamos el siguiente comando para configurar el repositorio:
```
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg]      https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

##  :large_blue_circle: Instalación Docker Engine
Actualizamos el índice del paquete apt e instalamos la última versión de Docker Engine, container y Docker Compose, o vaya al siguiente paso para instalar una versión específica:
```
  sudo apt-get update
```
```
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Para instalar una versión específica de Docker Engine, enumeramos las versiones disponibles en el repositorio, luego, seleccionamos e instalamos:


```
 apt-cache madison docker-ce
```
  ![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/versiones%20docker.png)

```
 sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
```
FOOOOTOOOOOOOOOO

Verificamos que Docker Engine esté instalado correctamente 
```
 sudo service docker start
```
Ejecutamos docker/getting-started, que lleva al tutorial de Docker 
```
 sudo docker run -d -p 80:80 docker/getting-started
```
FOOOOTOOOOOOOOOO

Ejecutamos nginx
```
  sudo docker run -p 8000:80 nginx
```
![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/run%20nginx.png)

Con el siguiente comando mostramos los contenedores que estan activos:
```
  sudo docker ps
``` 
  ![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/ps%202.png)

## :three: Descaga de nginx
 ![alt text](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c5/Nginx_logo.svg/220px-Nginx_logo.svg.png)
 ```
 sudo docker pull nginx
 ```
  ![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/pullnginx.png)

 ```
 sudo docker stop <CONTAINER ID>
 ```
 ```
 sudo docker rm <CONTAINER ID>
 ```
 ![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/stop%20y%20rm.png)
 
 Abrimos un navegador y ingresamos al localhost:8000 
 
 ![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/nginx.png)
 
 Al remover los contenedores aparece la tabla vacia
```
  sudo docker ps
``` 
 ![alt text](https://github.com/MargaritaMawyin/TutorialContenedorLinux/blob/main/ps%200.png)

 Referencias:
 https://docs.docker.com/engine/install/ubuntu/
 https://www.youtube.com/watch?v=mgwo8fq-SkA&t=130s
 
 

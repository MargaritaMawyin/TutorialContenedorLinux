# Uso de contenedor Docker con nginx

## Tutorial hecho con [WSL](https://learn.microsoft.com/en-us/windows/wsl/install )(Windows Subsystem for Linux). También se puede realizar en mäquinas virtuales como Virutal Box, Kali, etc.


 ## :one: Tener el WSL al día
 Configuracion del repositorio.
 

 ```
 sudo apt update
 ```
 ```
 sudo apt upgrade
```

## :two: Descarga del contenedor

En el entorno WSL descargamos  [Docker](https://docs.docker.com/engine/install/ubuntu/). 

Yo trabajé con Ubuntu,pero hay otras alternativas también
Actualizamos el índice de paquetes apt e instale paquetes para permitir que apt use un repositorio a través de HTTPS:
##   :large_blue_circle: Instalar usando el repositorio
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

##  :large_blue_circle: Installar Docker Engine
Actualizamos el índice del paquete apt e instalamos la última versión de Docker Engine, container y Docker Compose, o vaya al siguiente paso para instalar una versión específica:
```
  sudo apt-get update
```
```
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
Para instalar una versión específica de Docker Engine, enumeramos las versiones disponibles en el repositorio, luego seleccionamos e instalamos:


```
 apt-cache madison docker-ce
```

```
 sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
```
Verificamos que Docker Engine esté instalado correctamente ejecutando docker/getting-started, que lleva al tutorial de Docker.
```
 sudo service docker start
```
```
 sudo docker run -d -p 80:80 docker/getting-started
```

```
  sudo docker run -p 8000:80 nginx
```
```
  sudo docker ps
``` 
  
 Descaga de NDINX
 ```
 sudo docker pull nginx
 ```
 ```
 sudo docker stop <CONTAINER ID>
 ```
 
 ```
 sudo docker rm <CONTAINER ID>
 ```
 Referencias:
 https://docs.docker.com/engine/install/ubuntu/
 https://www.youtube.com/watch?v=mgwo8fq-SkA&t=130s
 
 

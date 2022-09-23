# Uso de contenedor Docker con nginx

# Tutorial hecho con WSL. Tambien se puede realizar en maquinas virtuales.

Primero
 Tener el WSL al dia
 ```
 sudo apt update
 ```
 ```
 sudo apt upgrade
```
Segundo

En el entorno WSL se descarga  ["Docker"](https://docs.docker.com/engine/install/ubuntu/). 

Yo trabajé con Ubuntu,pero hay otras alternativas tambien
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

```
 sudo mkdir -p /etc/apt/keyrings
 ```
 
 ```
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
 ```
 
 ```
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
  sudo apt-get update
```
```
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
```
 apt-cache madison docker-ce
```
```
 sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
```
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
 
 

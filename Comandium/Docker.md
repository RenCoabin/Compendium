- ¿Qué es docker?
Docker es un programa que permite ejecutar aplicaciones, como un ubuntu server mínimo, dentro de **contenedores**.

- ¿Cómo funciona?
Docker puede arrancar sistemas operativos mínimos (como si fuese una Raspberry Pi). Ejemplo:
<hr>
?Para descargar la imagen:
docker pull ubuntu:22.04 

?Arrancar servicio previamente con systemctl start/enable docker
<hr>
*En consola.*
- Para usar Docker sin *sudo*, añade tu usuario al grupo **docker**.

Después
<hr>
docker run -it --name (nombre) ubuntu:22.04

?"-it" modo interactivo con terminal
?"ubuntu:22.04" imagen a usar
<hr>
*En consola.*

- **Método de instalación**: pacman -S docker docker-compose

### !!!Recomendación:
	- Al entrar al servidor (en caso de):
		apt update
		apt install vim curl sudo
	- Para convertir un contenedor en imagen (guardarlo):
		docker commit (nombre) (nombre):personalizada
	- Para revisar los contenedores abiertos:
		docker ps -a
	- Para revisar las imágenes creadas y disponibles para usar:
		docker images
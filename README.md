# Agregar un HTML personalizado a en servidor web dockerizado Nginx

Esta práctica consiste en desplegar ngnix en un contenedor de Docker y mediante el uso de volúmenes agregar un archivo HTML que muestre mi nombre y apellidos (Xavier Borrás Mercant).

## Creación del contenedor
Iniciaremos la práctica creando el contendor con la imagen de nginx mediante el siguiente comando: 
`sudo docker run --rm -d -p 8080:80 --name web nginx`. Con este comando lo que hacemos es crear un contenedor de nginx con el nombre *web* en el puerto 8080.

![image](https://user-images.githubusercontent.com/91749310/174091218-f10bf012-3b27-4dea-9818-c76dcf78a612.png)

*Si no tenemos la imagen descargada Docker lo hará por nosotros.*

Para comprobar que nginx se ha instalado correctamente nos dirigimos a nuestro navegador y escribimos [http://localhost:8080](http://localhost:8080).

![image](https://user-images.githubusercontent.com/91749310/174103980-21d975c5-931c-48e0-9101-0a6f4aa5ffc5.png)

*Si todo está correcto debería aparecernos esta página de bienvenida a ngnix en nuestro navegador.*

A continuación deberemos parar nuestro contenedor con `sudo docker stop web`.

## Creación del HTML personalizado

Una vez hayamos visto que nginx funciona correctamente ha llegado el momento de agregar el HTML personalizado, para ello deberemos crear una carpeta en Documentos llamada nginx y otra site-content en su interior con el comando `sudo mkdir /home/xavier/Documentos/nginx` y  `sudo mkdir /home/xavier/Documentos/nginx/site-content`.

Nos situamos dentro de site-content con `cd /home/xavier/Documentos/nginx/site-content` y creamos un nuevo index.html con `sudo vim index.html` y en este caso, para la práctica tengo que poner mi nombre y apellidos.

![image](https://user-images.githubusercontent.com/91749310/174112313-65977fc6-f816-483d-91c0-6df4952e8a57.png)

(*En mi caso he copiado la estructura HTML de la página de bienvenida de nginx y  la he editado para poner mi nombre y apellidos*).

## Creación del volumen y comprobación final


A continuación deberemos usar este comando para crear un nuevo volumen y "dar de alta" la página web con nginx: 

    docker run --rm -d -p 8080:80 --name web -v /home/xavier/Documentos/nginx/site-content:/usr/share/nginx/html nginx

Para comprobar si se ha cambiado correctamente nos dirigimos nuevamente a [http://localhost:8080](http://localhost:8080):

![image](https://user-images.githubusercontent.com/91749310/174106515-d15d9e24-4b6c-4d42-9915-05307ab088ab.png)

*Como podemos observar el HTML ha funcionado y  muestra mi nombre y apellidos.*


## Conclusiones

Al igual que con la práctica de instalación y configuración de Docker, no fui capaz de realizarla en Windows 10 pero sí en Linux.

### Xavier Borrás Mercant - Sistemas Informáticos

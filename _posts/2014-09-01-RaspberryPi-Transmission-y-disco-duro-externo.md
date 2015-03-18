---
layout: post
title: "Raspberry Pi. Transmission y disco duro externo"
date: 2014-09-01 20:00:00
categories: linux
---

Hace poco al fín me decidí a comprar una raspberry pi. En este post voy a contar como la he configurado como servidor de descargas torrent.
Me he basado en estos apuntes dentro del foro de www.raspberrypi.org. Gracias desde aqui a todos los que aportan algo en este foro.

Nada más recibir la raspberry pi cogí una tarjeta sd de 4 GB que tenía sin usar con mi cámara reflex y le instalé raspbian, 
que es una modificación de debian adaptada a la raspberry pi. Enchufar cable de red ethernet, cable hdmi al tv, teclado usb, ratón usb, 
cargador usb (como el de los móviles), y listo. Solo queda la configuración inicial (expand sd, locale, etc) y ya tenemos una distribución linux corriendo.

Para las descargas estoy utilizando un disco duro externo autoalimentado de 250 GB LaCie que tenía conectado al ordenador de la tv.
Como lo voy a utilizar únicamente con la raspberry pi, lo he formateado con ext4, utilizando gparted como root en mi portátil con linux.
Para que no se reserve el 5% para root por defecto del formato ext4, debemos ejecutar (truco sacado de la web de Gregorio Espadas):

`sudo tune2fs -m 1.0 /dev/sda1`

Intentadolo desde la terminal con la rapsberry pi algo me fallaba y por no andar trasteando probé con gparted, y funcionó sin problemas.
Desde el terminal, sabiendo el nombre del dispositivo (por ejemplo sda) habría que ejecutar:

`sudo umount /dev/sda`
`sudo mkfs.ext4 -L nombre -I /dev/sda`

donde nombre es como queremos que se llame nuestro disco duro al montarse.
Creamos un directorio donde montar la partición:

`sudo mkdir /media/discoExterno`

montamos nuestro disco externo:

`sudo mount /dev/sda1 /media/discoExterno`

Ahora vamos a nuestro disco y creamos una carpeta para las descargas incompletas y otra para las completas:

`sudo mkdir /media/discoExterno/incomplete`
`sudo mkdir /media/discoExterno/complete`

y debemos darle a estas dos carpetas creadas permisos para que el usuario transmission pueda escribir en ellas.
Yo simplemente le he dado todos los permisos, pero se que esto no está muy bien hecho:

`sudo chmod 777 /media/discoExterno/incomplete`
`sudo chmod 777 /media/discoExterno/complete`

Una vez preparado nuestro disco externo para las descargas, es hora de intalar el demonio transmission. Para ello ejecutamos:

`sudo apt-get update`
`sudo apt-get install transmission-daemon`

te recomendará instalar tambien transmission-common y transmission-cli, decimos que si y ya está.

Ahora para configurar transmission, antes debemos parar el demonio que se nos ha inicializado en la instalación:

`sudo service transmission-daemon stop`

editamos el archivo de configuración:

`sudo nano /etc/transmission-daemon/settings.json`

debemos cambiar las siguientes lineas:

    "download-dir": "/media/discoExterno/complete",
    "incomplete-dir": "/media/discoExterno/incomplete",
    "rpc-whitelist": "127.0.0.1,X.X.X.X", (donde X.X.X.X es la direccion ip en la red de nuestra raspberry pi)
    "rpc-whitelist-enable": false

(para habilitar el acceso por web)

Podemos modificar más parámetros, pero no voy a entrar en ellos. Mejor echales un vistazo que tampoco son dificiles de entender.

Ya podemos inicializar de nuevo el demonio transmission:

`sudo service transmission-daemon start`

Con ello ya podemos entrar en transmission desde cualquier navegador web introduciendo X.X.X.X:9091 (donde X.X.X.X es la ip de la raspberry pi)
Yo tambien accedo a través de mi tablet con android con el programa ATG, con el que puedo gestionarlo igual que desde un navegador.

A partir de este momento solo queda descargar y compartir con todos.

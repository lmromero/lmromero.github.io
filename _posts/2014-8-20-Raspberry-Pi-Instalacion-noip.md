---
layout: post
title: Raspberry Pi. Instalar el servicio noip. 
date: 2014-08-20 13:00
categories: jekyll update
---

Para tener acceso a nuestra raspberry pi desde cualquier sitio a través de internet, es necesario tener instalado un servicio como el que ofrece noip. Lo que conseguimos con este servicio es poder asociar un nombre de host (más fácil de recordad) a nuestra ip (difícil de recordar y dinámica). Por supesto en primer lugar hay que configurar ese host en la web de noip.

Ahora instalaremos un cliente noip para linux en la raspberry pi, y conseguimos que cada cierto tiempo se actualice nuestro nombre de host con la ip que tengamos en cada momento. Los pasos a seguir son los siguientes:

    Accedemos por ssh a nuestra raspberry pi, si es que no la tienes conectada a teclado ni monitor alguno, como es mi caso.
    Instalamos y configuramos el cliente.

    cd /usr/local/src
    sudo wget http://www.noip.com/client/linux/noip-duc-linux.tar.gz
    sudo tar zxf noip-duc-linux.tar.gz
    cd noip-XXX
    sudo make
    sudo make install

    Durante la instalación te pedirá tu usuario de noip y su contraseña, además del intervalo de actualización.
    Si quieres que se inicie el servicio cada vez que enciendas la raspberry pi, creamos el siguiente script, lo ponemos en

    /etc/init.d/

    y lo registramos al inicio

    sudo nano /etc/init.d/noip2

    . El contenido del script descargado de aqui, es:

    #! /bin/sh
    # /etc/init.d/noip
    ### BEGIN INIT INFO
    # Provides: noip
    # Required-Start: $remote_fs $syslog
    # Required-Stop: $remote_fs $syslog
    # Default-Start: 2 3 4 5
    # Default-Stop: 0 1 6
    # Short-Description: Simple script to start a program at boot
    # Description: A simple script from www.stuffaboutcode.com which will start / stop a program a boot / shutdown.
    ### END INIT INFO
    # If you want a command to always run, put it here
    # Carry out specific functions when asked to by the system
    case "$1" in
    start)
    echo "Starting noip"
    # run application you want to start
    /usr/local/bin/noip2
    ;;
    stop)
    echo "Stopping noip"
    # kill application you want to stop
    killall noip2
    ;;
    *)
    echo "Usage: /etc/init.d/noip {start|stop}"
    exit 1
    ;;
    esac
    exit 0

    Hacemos el script ejecutable:

    sudo chmod 755 /etc/init.d/noip2

    Y registramos el script para que se ejecute al comiezo:

    sudo update-rc.d NameOfYourScript defaults

Quedaría redireccionar los puertos en nuestro router para que apuntaran a la ip interna de nuestra raspberry pi. Pero en este temo no voy a entrar en este post.
Con todo esto conseguimos que la raspberry pueda ofrecer servicio como owncloud, servidor web, gestionar tus descargas transmission, etc.
Un saludo.

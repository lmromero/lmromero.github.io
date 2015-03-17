---
layout: post
title: "Debian en Asus eee pc 1005P"
date: 2014-09-01 20:23:00
categories: linux
---

Le he instalado a una amiga debian en su netbook (modelo Asus Eee Pc 1005P).
Después de pensar y buscar un poco por internet, me decidí por debian porque al ser la que utilizo, es la distribución que creo 
domino mejor, y en caso de necesitar ayuda, seguro que podré ayudarle.
Decidí instalar, desde un pendrive usb y el netbook conectado por ethernet a mi red, el sistema base, sólo añadiendo ssh y
utilidades para portátil, para posteriormente instalar las aplicaciones realmente necesarias. Al instalar el gestor de arranque
(grub) en la instalación debes tener cuidado porque puede intentar instalarlo automáticamente en un lugar que no es el adecuado.
Es mejor, cuando el sistema pregunte si quieres instalar grub, decir que no, e instantáneamente abre otra pantalla preguntando dónde 
instalarlo. En mi caso tuve que poner ‘/dev/sdb’ porque si no, me lo instalaba en /dev/sda que era el propio pendrive usb que estaba
usando para instalar. Esta solución la encontré después de dos instalaciones fallidas y un poco de búsqueda por internet, y 
la comparto por si alguien llega a tener el mismo problema.

Mucha de la información de la configuración e instalación de paquetes la encontré en Takla’s Weblog (en inglés). Dónde se explica 
la instalación de debian wheezy en un Asus Eee Pc 1005P.

Un problema que me encontré fue que el brillo de la pantalla no se podía poner al máximo, quedando algo oscura cuando la luz 
ambiental es buena. Para solucionarlo hay que hacer lo siguiente:
En un terminal poner

`nano /etc/default/grub`

cambiar la línea

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`

por

`RUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"`

guardar, y ejecutar

`update-grub`
`reboot`
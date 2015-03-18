---
layout: post
title: "Raspeberry Pi. Crear tu propia nube con Owncloud"
date: 2014-09-12 12:00
categories: linux
---

Si quieres tener tu propia nube, con tus archivos privados, en tu propio servidor, puedes utilizar [owncloud](http://owncloud.org) instalado en 
una [raspberry pi](http://raspberrypi.org).
Como consume poco y puede dejarse encendida, se hace ideal, siempre dentro de las limitaciones del aparato, para actuar como servidor casero.
Si además tiene un disco duro externo puedes conseguir una buena capacidad de almacenamiento, seguro que más de lo que te ofrecen algunas empresas como 
[dropbox](www.dropbox.com), 
y para ser algo “casero” no funciona nada mal.

En [instructables](http://www.instructables.com/id/Raspberry-Pi-Owncloud-dropbox-clone/) (link en inglés) puedes encontrar la guía que seguí yo para la instalación.
Está todo perfectamente explicado y viene con capturas de pantallas.

Si tu raspberry pi está detrás del router de tu operador, para poder acceder a owncloud desde internet habrá que redireccionar los puertos apropiados
en el router hacia la ip, que debe ser estática, de la raspberry pi. Si además la ip que te proporciona el operador es dinámica, puedes utilizar servicios 
como [no-ip](http://noip.com) y crear tu propio dominio gratuito que te redirecciona a la ip de tu router en ese momento.

Owncloud es software libre y tiene cliente para linux, mac y windows, además de para android e ios.
---
layout: post
title: "Debian. Cambiar tamaño terminal en debian"
date: 2014-08-20 17:00:00
categories: linux
---

Si cada vez que abres un terminal y redimensionas la ventana porque no te gusta trabajar con el tamaño que viene predefinido,
puedes cambiarlo para que siempre se abra con el tamaño deseado de la siguiente forma (para el emulador de terminal xfce en debian):

`sudo nano ~/.config/Terminal/terminalrc`

En la linea `MiscDefaultGeometry\=80×24` cambia los valores por los que quieras.

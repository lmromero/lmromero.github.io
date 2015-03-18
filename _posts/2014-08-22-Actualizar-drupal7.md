---
layout: post
title: "Actualizar Drupal 7"
date: 2014-08-20 15:30:00
categories: gnu
---

Realizar una actualización de seguridad del core de Drupal (dentro de la versión 7). Los pasos a seguir son los siguientes:

1. Poner tu sitio en modo mantenimiento.
2. Realizar una copia de seguridad y descargar la actualización de drupal necesaria. Puedes ver la versión en Informes -> Actualizaciones disponibles.
3. Acceder por ftp a tu servidor (yo utilizo Filezilla para realizar este paso). Reemplazar todas las carpetas y ficheros en la raiz del sitio drupal, excepto la carpeta Sites.
4. Ejecutar el script de actualización de la base de datos.
`www.lmromero.com/update.php` (en mi caso).

Si tienes el alojamiento con [1and1](http://1and1.es) como es mi caso, debes descomentar una línea del fichero `.htaccess`, quedando de la siguiente manera:
    
    # If your site is running in a VirtualDocumentRoot at http://example.com/
    # uncomment the following line:
    RewriteBase/

Sin este último paso, aparece un problema de error 500 al intentar acceder a cualquier lugar de tu web.

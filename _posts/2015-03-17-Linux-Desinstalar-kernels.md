---
layout: post
title: "Linux. Desisntalar kernels y eliminarlos de Grub"
date: 2015-03-17 16:37:00
categories: linux
---

Conocer el kernel que estamos usando: `uname -r`

Saber los kernels que tenemos instalados: `dpkg --get-selections | grep linux-image`

Desinstalar el kernel que no queremos: `apt-get remove --purge linux-image-XXXXX`

Actualizar grub para los nuevos kernels: `update-grup`
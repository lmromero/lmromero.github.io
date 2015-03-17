---
layout: post
title: "Juego. Cifras y letras."
date: 2014-08-20 18:25:00
categories: programacion
---

Ordenando y tirando papeles antiguos me he encontrado un folio con el código fuente del juego “Cifras y Letras”.
Es un programa que escribió, seguramente, mi primo Oscar hace ya unos 20 años o más. Está escrito en Basic y lo hacíamos 
funcionar en un ordenador Amstrad CPC 464 de monitor verde. Como no quiero perder este documento, he pensado compartirlo en este blog.
No he probado si funciona implementandolo por ejemplo en Gambas pero cuando tenga un poco de ganas y tiempo, lo haré.

El código es el siguiente:

    10 CLS:RANSOMIZE:CLS
    20
    30 LOCATE 3,3:INPUT "JUGADOR 1";A$
    40 LOCATE 5,3:INPUT "JUGADOR 2";B$
    50 LOCATE 7,3;INPUT "JUGADOR 3";C$
    60 CLS
    70 A=0:B=0:C=0:P=1
    80 IF P=11 THEN 130
    90 LOCATE 2,30:PRINT "PRUEBA ";P
    100 IF P=1 OR P=3 OR P=5 OR P=7 OR P=9 THEN Z=1: LOCATE 2,10:PRINT "LETRAS" ELSE Z=2: LOCATE 2,10:PRINT "CIFRAS"
    110 IF Z=1 THEN 210
    120 IF Z=2 THEN 410
    130 CLS
    140 LOCATE 3,3:PRINT A$;" TIENE ";A;" PUNTOS"
    150 LOCATE 5,3:PRINT B$;" TIENE ";B;" PUNTOS"
    160 LOCATE 7,3:PRINT C$;" TIENE ";C;" PUNTOS"
    170 LOCATE 11,3
    180 IF A&amp;gt;B AND A&amp;gt;C THEN PRINT A$;" GANA.":END
    190 IF B&amp;gt;A AND B&amp;gt;C THEN PRINT B$;" GANA.":END
    200 PRINT C$;" GANA.":END
    210 X=3:FOR F=1 TO 9
    220 LOCATE 7,3:INPUT "VOCAL (V) O CONSONATE (C)";S$
    230 IF S$="V" THEN H=INT (RND*5):GOSUB 300:GOTO 260
    240 IF S$="C" THEN GOSUB 360:GOTO 260
    250 GOTO 220
    260 LOCATE 10,X:PRINT X$
    270 X=X+2
    280 NEXT F
    290 LOCATE 15,3:PRINT "PULSA UNA TECLA PARA EMPEZAR":LET R$=INKEY$:IF R$="" THEN 290
    300 GOTO 480
    310 IF H=1 THEN X$="E"
    320 IF H=0 THEN X$="A"
    330 IF H=3 THEN X$="O"
    340 IF H=2 THEN X$="I"
    350 IF H=4 THEN X$="U"
    360 RETURN
    370 Q=INT (RND*26)+65
    380 IF Q=65 OR Q=69 OR Q=73 OR Q=75 OR Q=79 OR Q=85 OR Q=87 OR Q=72 OR Q=88 OR Q=81 OR Q=89 THEN 370
    390 X$=CHR$ (Q)
    400 RETURN
    410 LOCATE 8,3:PRINT "LAS CIFRAS SON: "LOCATE 10,3
    420 FOR U=1 TO 6
    430 GOSU 620
    440 PRINT O;" ";
    450 NEXT U
    460 LOCATE 12,3:PRINT "PULSA UNA TECLA PARA EMPEZAR":J$=INKEY$:IF J$="" THEN 460
    470 L=INT (RND*999)+1:LOCATE 15,3:PRINT "LA CIFRA A CONSEGUIR ES ";K
    480 GOTO 490
    490 BEEP:GOSUB 710:BEEP
    500 CLS
    510 LOCATE 3,3:PRINT "SE ACABO EL TIEMPO"
    520 LOCATE 5,3:IF P=1 OR P=4 OR P=7 OR P=10 THEN PRINT "EL TURNO ES DE ";A$
    530 IF P=2 OF P=5 OR P=8 THEN PRINT "EL TURNO ES DE ";B$
    540 IF P=3 OR P=6 OR P=9 THEN PRINT "EL TURNO ES DE ";C$
    550 LOCATE 7,3:INPUT "QUIEN HA GANADO";Z$
    560 IF Z$=A$ OF Z$=B$ OR Z$=C$ THEN GOTO 570 ELSE GOTO 550
    570 LOCATE 9,3:INPUT "CON CUANTOS PUNTOS";W
    580 IF Z$=A$ THEN A=A+W
    590 IF Z$=B$ THEN B=B+W
    600 IF Z$=C$ THEN C=C+W
    610 CLS:P=P+1:GOTO 80
    620 O=INT (RND*16)+1
    630 IF O=11 THEN O=15
    640 IF O=12 THEN O=25
    650 IF O=13 THEN O=30
    660 IF O=14 THEN O=50
    670 IF O=15 THEN O=75
    680 IF O=16 THEN O=100
    690 RETURN
    700 RETURN
    710 LOCATE 17,20:PRINT "SEGUNDOS:"
    720 FOR T=0 TO 45
    730 LOCATE 17,36:PRINT T
    740 FOR G=1 TO 1720:NEXT G
    750 NEXT T
    76O RETURN
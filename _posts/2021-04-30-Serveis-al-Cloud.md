---
layout: post
title: El Cloud i els backups
subtitle: La segura inseguretat del Cloud
cover-img: /assets/img/CloudBackup-Cover.jpeg
thumbnail-img: /assets/img/CloudBackup-thumb.png
share-img: /assets/img/CloudBackup-Cover.jpeg
tags: [cloud, backup, seguretat]
---

<p align="justify">Els núvols semblen navegants solitaris aliens a qualsevol incidència que passa a les profunditats de les comunitats indígenes, que viuen despreocupades i quan més els convé reclamen aquella pluja tant necessària per la seva subsistència amb balls exòtics i connexions desenfrenades. Balls que semblen més pensats per distreure a la pròpia comunitat que no pas per atreure l’atenció d’uns núvols que continuen navegant per sobre els seus caps, sense perdre ni tan sols uns segons en escoltar la música.</p>

<p align="justify">La pandèmia sembla haver despertat un interès adormit per la computació al Cloud. Una computació que abdueix als indígenes amb caramels com la versatilitat, alta disponibilitat, etc. En aquest afany de pujar al cavall guanyador, molts entenen el Cloud com quelcom aliè a qualsevol incident de seguretat i què, per tant, no requereix de còpies de seguretat. El Cloud pot amb tot: Segur?</p>

<p align="justify">El primer que cal fer al contractar un <b>servei al Cloud</b> és llegir bé la lletra petita i tenir molt present quines són les <b>polítiques de còpies de seguretat</b> que adopta el servei contractat, o per més seguretat, adoptar una política de còpies pròpia tenint molt present la regla del 3,2,1.</p>

<p align="justify">Un exemple clar, el podem trobar en la plataforma GitHub. Quants usuaris i empreses tenen el codi emmagatzemat a <b>GitHub</b>? i de tots/es aquests/es, quants/es realitzen backups dels repositoris i la resta d’informació del seu perfil?</p>

<p align="justify">Tenir el codi a GitHub ens assegura disponibilitat i versatilitat, entre moltes altres coses, però no ens assegura la seva disponibilitat davant d’un incident de seguretat, a no ser què, tinguem una política de còpies de seguretat implantada.</p>

<p align="justify">De polítiques de còpies de seguretat n’hi ha tantes com colors, i tant diverses com les llengües que es parlen arreu. Però, un exemple molt senzill de com tenir una còpia en local del perfil de GitHub de la nostra organització, podria ser la següent:</p>

<p align="justify">Connectar-nos a Github des d’un servidor de l’organització, obtenir totes les dades del perfil juntament amb els repositoris, empaquetar-ho i introduir aquests fitxers dins la política de còpies de seguretat de l’organització.</p>

<p align="justify">Un cop tenim el procediment clar, passem a programar-lo perquè pugui ser automatitzat. En aquest cas, he escollit realitzar la tasca amb un contenidor Docker realitzat per l’usuari [Vic Shóstak](https://github.com/koddr){:target="_blank"} i que he adaptat una mica per tal d’afegir-hi una funció de Python que permeti enviar la notificació del backup a un canal de Teams.</p>

Els passos son molt senzills:  
1. Quan s’executa el contenidor, s’inicia amb un script que entra en bucle i, un cop al dia, executa la tasca de connectar-se al nostre compte de GitHub, gràcies a aquest fantàstic projecte, [projecte python](https://github.com/josegonzalez/python-github-backup){:target="_blank"}, i descarrega i empaqueta el contingut a la ubicació local indicada.  
2. Desprès d’empaquetar la còpia envia un missatge al compte de Teams.  
3. I per finalitzar, elimina els fitxers de les còpies antigues.  
4. Degut a què el servidor Docker està inclòs dins la política de còpies de seguretat de l’organització, 	ja tenim còpies del codi amb un risc, la pèrdua de la informació d’un dia, acceptable en aquest cas.

<p align="justify">El projecte té molts punts a millorar però, inicialment, compleix amb la funció principal de tenir còpies del codi font. Si vols veure més en detall com ha quedat el projecte, al final de l'article en l'apartat de recursos pots consultar-lo.</p>

<p align="justify">I recorda, més val prevenir els períodes de sequera, que refiar-se de xamans acrobàtics que diuen saber més del què realment saben.</p>

**Recursos**  
1. [Projecte amb python](https://github.com/josegonzalez/python-github-backup){:target="_blank"}
2. [Projecte modificat](https://github.com/jordimalla/github-backup-automation){:target="_blank"}

**Imatges de**  
1. [thumbnail](https://www.backupassist.es/plugin-para-remote-backup-cloud/){:target="_blank"}  
2. [cover](https://www.magiconline.es/cloud/copia-de-seguridad-en-la-nube-como-funciona/){:target="_blank"}

---
title: Hack the box - Curling.
date: 2019-04-01
---

Haremos el seguimiento para poder hackear la máquina Curling de Hack The Box. La máquina ya se encuentra retirada de la lista activa, asi que podemos liberar su seguimiento hacking.

<img class="center" src="/images/curling_1.png" />

Para empezar, haremos NMAP sobre la IP del sitio, esto nos devolvera los puertos disponibles para la IP proporcionada:

<img class="center" src="/images/curling_2.png" />

Encontramos el puerto 80 y el puerto 22 abierto. Al visitar el sitio nos podemos dar cuenta que es un Joomla.

<img class="center" src="/images/curling_3.png" />

Después de hacer algunas busquedas y reconocimiento dentro la IP podemos ver algo raro en el "source code", hay un secret.txt.

<img class="center" src="/images/curling_4.png" />

Al ver el secret.txt nos podemos dar cuenta que es un base64, asi que procedemos a hacerle un decode.

<img class="center" src="/images/curling_5.png" />

Esto podría ser un pass, asi que procedemos a buscar un username. Joomla tiene algunos posts, asi que al ver el autor de esos Posts podemos darnos cuenta que el username es "Floris"

<img class="center" src="/images/curling_6.png" />

Procedemos a hacer login dentro el Administrador Joomla y efectivamente, esas son las credenciales correctas.

Utilizamos un <a href="https://github.com/rootphantomer/hack_tools_for_me/blob/master/Joomla-Shell-Upload.py">Joomla shell up</a> Y procedemos a subir una Shell

<img class="center" src="/images/curling_7.png" />

Haciendo un poco de enumeración, podemos ver que existe una archivo llamado password_backup

<img class="center" src="/images/curling_8.png" />

Al descargarlo, podemos darnos cuenta que es un "hex dump file".

<img class="center" src="/images/curling_9.png" />

Al ser un hex dump, lo que procedemos hacer es convertirlo a un binario para poder ver de que se trata el archivo.

<img class="center" src="/images/curling_10.png" />

Nos podemos dar cuenta que es un archivo bzip2 comprimido. Al descomprimir con ayuda de bzip2 podemos ver que nos da un archivo comprimido GZip, procedemos a descomprimirlo y nos da un archivo de nuevo bzip2.

<img class="center" src="/images/curling_11.png" />

Despues al descomprimir, nos da un archivo TAR, despues al descomprimir nos da un archivo de text llamado password.txt

<img class="center" src="/images/curling_12.png" />

Al ocupar dicho password en un ssh podemos hacer login con el usuario floris.

<img class="center" src="/images/curling_13.png" />

Podemos hacer un cat al user.txt sin problemas.

<img class="center" src="/images/curling_14.png" />

Ya tenemos el user!

Ahora bien, mirando y haciendo enumeración dentro del server, podemos ver que hay una carpeta llamada "admin-area", el cual tiene dos archivos, input y report. Al revisar un poco estos archivos se comportan de manera en que lo que se hay en en el archivo input (normalmente una URL), se imprimie en el report (todo el html de la URL).

<img class="center" src="/images/curling_15.png" />

Con esto en cuenta, podemos deducir que si escribimos en URL un path local, entoncesmuy posiblemente obtendremos su contenido.  

<img class="center" src="/images/curling_16.png" />

Con esto, podremos obtener root.txt!!

Gracias por leer!

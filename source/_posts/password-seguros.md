---
title: Passwords seguros y buenas prácticas.
date: 2017-05-30
---

Hoy en día tener muchas cuentas de usuario y password seguras en muchos sitios web se ha convertido en una necesidad. La seguridad de todas nuestras cuentas de internet debe ser uno de los puntos más importantes en este tema. Explicaré el método que uso para almacenar todas mis cuentas y generar passwords seguros.

La mayoría de los sitios de internet siempre se autentifica con un email y un password, regularmente usamos una cuenta de correo para casi todos los sistemas que necesitamos registrarnos. Es por eso que nuestro email debe ser el más seguro de todas nuestras cuentas ya que si por alguna razón perdemos acceso en algún sitio, siempre podemos recuperar la contraseña mediante nuestro email. Lo más recomendable es activar <a href="https://www.google.com/landing/2step/">"Two Factor Authentication"</a> para nuestro email. Así, si alguien toma nuestro password de nuestro email, es necesario contar con nuestro dispositivo movil para que pueda acceder. Es muy importante entender el tema de "Two Factor Authentication" ya que en muchos sistemas se puede habilitar, por ejemplo Facebook, Paypal, Amazon, etc.

No confio en ningún  <a href="http://www.pcmag.com/article2/0,2817,2407168,00.asp"> "password manager"</a> existente en Internet. Hay que estar muy atentos para ver como esas empresas hacen su trabajo, y al estar muchas personas involucradas en el desarrollo de ese tipo de sistemas (desarrolladores de software, administradores de sistema, etc), entonces pueden ser vulnerables de alguna manera. Tenemos un ejemplo de una empresa encargada de guardar los passwords de muchos usuarios <a href="http://lifehacker.com/lastpass-hacked-time-to-change-your-master-password-1711463571">LastPass</a> los cuales fueron hackeados, no importa de que magnitud fue el problema, lo importante es saber que de alguna manera puede ser vulnerable en terminos de seguridad.

Así que para almacenar todas mis cuentas uso <a href="https://www.keepassx.org/">KeePass</a>. KeePass es un software el cual se instala en tu computadora y genera un archivo con extension ".kdbx". Al crear una base de datos de usuarios/passwords te pide una contraseña maestra la cual es para abrir el archivo y puedas ver toda la información de tus cuentas.

Ahora, solo es necesario tener el archivo *.kdbx para poder abrirlo en cualquier computadora o telefono (<a href="https://itunes.apple.com/mx/app/minikeepass-secure-password-manager/id451661808?mt=8">KeePass for IOS</a>) entonces lo que hago es compartir el archivo en todos lados via DropBox. Cabe mencionar que para <a href="https://www.dropbox.com/help/security/enable-two-step-verification">DropBox tengo habilitado Two Factor Authentication</a>. Además, es importante señalar que cada password debe ser diferente de cada cuenta, ahora tenemos un programa que las guarda por nosotros así que no es necesario memorizarlas.

Como veras, el archivo se comparte en todos mis dispositivos y puedo abrirlo y editarlo sin problemas. Además este archivo es para mi uso interno, ningúna empresa, ningún tercero puede acceder a mi cuenta.

No olvidar que en la mayoria de todas nuestras cuentas se usa el email, entonces si por alguna razón perdemos todo, el email va a ser la clave para recuperar todas nuestras cuentas.

Un tip, para los passwords uso largas frases que sean fáciles de recordar para el humano, <a href="https://theintercept.com/2015/03/26/passphrases-can-memorize-attackers-cant-guess/">acá dejo un post</a> muy interesante acerca del tema. Así, puedo usar por ejemplo "Los Niños Son Pequeños", esta frase computacionalmente es muy complicada ya que tiene mayusculas, minusculas, espacios y son muchas letras.

En este <a href="https://howsecureismypassword.net/">sitio de internet</a> pueden  evaluar sus passwords.

---
title: Mocking testing con Python
date: 2013-06-11
---

Ahora traigo un tema muy interesante el cual es <a href="http://www.voidspace.org.uk/python/mock/">mocking testing para python</a>. Esto es una herramienta para Testing. El testing de nuestro código no siempre es muy valorado sin embargo es muy eficaz si escribimos un script a base de Testing, normalmente existen ciertos aspectos los cuales hay que estar muy seguro de que la app o script este funcionando como nosotros queremos sin presentar algún error extraño el cual el usuario lo vea y no sea digerible, alguna vez han visto un error no controlado por parte de google por ejemplo y dejen ver un vomito de código y errores?.


Básicamente lo que hace esta libreria de Testing es reemplazar partes del codigo que estamos Testeando con objetos simulados y así simular la forma de respuesta de ciertas funciones. Por así decirlo parchamos una clase o función e introducimos algo que nosotros queramos. El ejemplo que aquí expondré es que imaginemos que tenemos una clase el cual consulta los Tweets de una cierta cuenta y no los trae en formato JSON, ahora nosotros cachamos la info y calvez convertimos esa info en objetos u algo para posterior manejo. Aquí realizamos un request a una url por ejemplo <a href="http://search.twitter.com/search.json?q=tonsquemisa&count=5"></a>http://search.twitter.com/search.json?q=tonsquemisa&count=5 y esta URL como verán el formato que nos regresa es JSON.

Ahora imaginemos que por circunstancias ajenas la URL no funciona, simplemente los <a href="http://status.twitter.com/">servidores de Twitter</a> por alguna razón sufrieron algún daño nuclear y no regresa nada de nada, después nuestro script al consultar esa URL simplemente no regresara nada y tal vez se caiga nuestro script, para esto hay que estar preparados en nuestro cliente Twitter y poder cachar este error y realizar alguna acción la cual ayude a que el usuario no se quede así nomas con un vomito de errores, es aquí donde entra el Testing apoyándose con mock :D.

Escribí un <a href="https://github.com/misalabs/python_mock">pequeño ejemplo</a> el cual podrán visualizar la idea de lo que Mock hace. Tenemos una clase la cual hace la consulta a Twitter y podemos ver que cachamos varios aspectos que es el RequestException, ConnectionError y el status code. Ahora imaginemos que esta clase es un modulo principal en alguna app mucho mas grande y por cuestiones ajenas la consulta a la URL falla y simplemente no podemos conectarnos, debemos estar seguros que se realizara alguna acción digerible para el usuario y pues debemos escribir un Test para probar el código, es eso o hackear por algún momento los servidores de Twitter y tirarlo y así probar nuestro script XD, lo que se les haga mas fácil. Tenemos también un test el cual probaremos la eficacia de nuestro script y es ahí donde Mock entra.

Podemos ver en esta <a href="https://github.com/misalabs/python_mock/blob/master/tests.py#L14">linea</a> como recorremos todas las posibles excpeciones RequestException, Timeout, ConnectionError en las que puede caer un Request y probamos que todas sean cachadas correctamente.

Después por ejemplo en esta <a href="https://github.com/misalabs/python_mock/blob/master/tests.py#L22">linea</a> enviamos un status code 403 y probamos que ese estatus esta cachado correctamente en nuestro script.

Como verán es un ejemplo muy sencillo pero muy eficaz para probar 2 aspectos, la funcionalidad de mock y la importancia del testing  aqui hice uso de ciertas librerias sin embargo lo mas importante es entender la idea de Mock y Testing. Existen <a href="http://es.wikipedia.org/wiki/Desarrollo_guiado_por_pruebas">tecnicas de testing</a> las cuales debiesen saber si se dedican a escribir código, no necesariamente debemos ser expertos en Testing sin embargo debemos conocer bases las cuales ayuden a que el código sea mas 'verynice' :0

Como verán el código se encuentra en <a href="https://github.com/misalabs/python_mock">Github</a> y escrito en Python, ademas de que use la librería mock para python, request para consumir la URL de Twitter y unittest para las pruebas. Librerías así debiesen estar en varios lenguajes para realizar Testing a su código y si no existen inventenlas ahahaha. Y pues anímense a realizar un Fork para mejorar el código :D

<img class="center" src="/images/mock_python.png"/>

* Actualización 2013-07-05, con las nuevas reglas en el API de Twitter ahora es necesario una autenticidad en el GET, algo así, después cuando me de tiempo mueva el ejemplo a otra instancia API como en Youtube o algo así. Aun así el ejemplo actual sirve muy bien para entender el funcionamiento de Mocking.

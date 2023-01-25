---
title: Chat con comet en PHP
date: 2012-11-12
---

Buscando diversas técnicas sobre comunicación asincrona nos encontramos con Comet, esta técnica funciona muy similar a AJAX, es decir, la comunicación con el servidor la mantenemos teniendo así una conexión HTTP de larga duración, reduciendo asi el tiempo de latencia.

En este metodo el cliente no esta revisando constantemente si el servidor tiene algo "nuevo" para nosotros si no que el servidor abre una línea de comunicación y cuando exista una "nueva información" se la pasa al cliente.

Un ejemplo muy en básico es la idea de un Chat, en la antiguedad {ahaha} se usaba una cierta técnica llamada <a href="http://es.wikipedia.org/wiki/Polling">"Pooling"</a>  el cual se realizaba una consulta constantemente en busca de información nueva, esto es algo pobre ya que aumentamos las peticiones hacia el servidor aunque este no tenga nada nuevo que entregarnos, pufff. Aqui vemos como implementan este tipo de <a href="http://chategory.com/chategories/android/">técnica llamada Pooling</a>, amm si abren la consola de Chrome "F12" se vera que estan corriendo 3 archivos que son "getNumberOfUsers.php" "isTyping.php" y "listenToRecive.php", así a ojo de buen cubero se puede ver que uno es para obtener el numero de usuarios, otros para ver si alguiene sta escribiendo y otro es para recibir los mensajes, ahahah son muchos archivos, además de un constante "pedir" al servidor, lo cual es mucho desmán.

Ahora imaginense algo como Facebook, ustedes abren la página y se ponene a hacer cualquier otra cosa y vuelven a la pestaña de Facebook y aparecene "nuevas" noticias, pues es algo similar, en cuanto el servidor tenga nuevas noticias o mensajes o  lo que sea el servidor envia la información al cliente osea nosotros y así sin nosotros estar realizando peticiones manuales o programadas. Bueno bueno todo esto de que el servidor nos envie datos se llama HTTP Push :D.

Para no hacerselar tan larga, además de que hay muchos ejemplos en la gran red dejare un ejemplo de implementación de un Chat con Comet en PHP, por ahi dejare también los <a href="https://github.com/misalabs/chat-comet">códigos</a> paque lo disfruten :D. Cabe aclarar que si monitorean los archivos "F12" en Google Chrome se puede ver como se corta la petición que se hace al servidor, esto es basicamente la configuración del servidor y pues precisamente se hace para no crear bucles infinitos los cuales afecten el funcionamiento del servidor ;).

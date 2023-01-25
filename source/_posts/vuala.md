---
title: ChatRuleta, XMPP y JQuery
date: 2013-05-27
---

Muy bien, hace ya un tiempo estaba interesado en sistemas de comunicación así que me metí en diversos aspectos entre ellos <a href="http://blog.misalabs.com/que-es-xmpp-y-bosh-ejabberd/">XMPP</a> y pues entre mi búsqueda de la verdad desarrolle un ChatRuleta con este tipo de tecnología. Hay que destacar que XMPP y demás es necesario una configuración chingona para levantar todo pues como lo habíamos visto, HTTP lo convertimos en una especie de conexión de petición y respuesta.

En este ejemplo use <a href="http://strophe.im/">Strophe</a> que es una librería para poetas del XMPP XD, específicamente se uso la librería en Javascript. El sistema lo que hace es entrar a una sala de Chat y conversar con alguien de manera Random. Aquí para el vídeo se uso un proyecto libre que es <a href="http://code.google.com/p/flash-videoio/">Flash-VideoIO</a>.

Si lo que quieren es correrlo de manera local o en un VPS, lo que sea, es necesario configurar muy bien el servidor ejabberd ya que es lo principal para que todo funcione correctamente. Ademas es necesario habilitar MUC XEP-0045 y In-Band registration XEP-0077, dense una vuelta en Google sobre como habilitar esto en ejabberd. muy fácil es solo habilitar un par de linea en la configuración.

Este tipo de tecnología podría llamarla como innovadora en estos tiempos de locura, Web 2.0 y conexiones en tiempo real. Ademas de que es un protocolo abierto, varios lo usan y pueden entenderlo por ejemplo Google Talk, se puede hacer varias cosas las cuales podrían ser muy interesantes, el limite es el cielo ahaha.

Aqui podemos ver una imagen de la pagina de inicio del chat.

<img class="center" src="/images/vuala_2.png" />

Y pues esta es otra del Chatruleta, conmigo mismo ahaha.

<img class="center" src="/images/vuala_2.png" />

Y aquí muy importante es que se deja abierto un canal escuchando, en espera de recibir nuevos mensajes en el chat :D

<a href="https://github.com/misalabs/vuala">El código esta en Github</a>, si tienen alguna duda de como correrlo pues no duden en contactarme :D...

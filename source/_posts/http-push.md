---
title: HTTP Push con Python/Django, StropheJS y Ejabberd
date: 2013-12-02
---

Hace tiempo ya habia estado hablando de las formas de comunicación entre cliente y servidor las cuales hoy en dia es imprescindible hacer uso de técnicas que ayuden a una comunicación asincrona entre el propio server-cliente/cliente-server.

<a href="http://es.wikipedia.org/wiki/Tecnolog%C3%ADa_Push">El HTTP push</a>  es una comuncación entre el server y el cliente, sin que el cliente se la pida. Imaginemos que en Facebook existe una nueva publicación de algún amigo, entonces si nosotros recargar la página (request al server) Facebook nos envia esa info, simplemente se actualiza nuestro Wall. Como diablos es posible esto?!!!, pues gracias a que Facebook hizo un HTTP Push desde el server hacia nosotros como clientes. Muy simple el concepto.

Hace mucho tiempo a nadie se le ocurrio que se pudiese enviar info del server al cliente sin que el cliente se lo pida, entonces se creo el protocolo HTTP sin esta funcionalidad. Ahora muchos han querido implementar este tipo de técnica pero no es un estandar, estan en proceso de que se implementen sockets en HTML pero pues en lo que se vuelve un estandar mucho han creado sus formas.

Hace tiempo yo hable un poco del tema del uso de XMPP y como con ayuda del protocolo pude hacer un chat, este chat es a base de notificaciones, es decir, se mantiene un canal abierto hasta que algun usuario introduzca un mensaje.

En este ejemplo la idea base sera: un cliente abre un sitio web, despues el server si tiene un nuevo registro en la BD le avisara el cliente sin que el cliente se lo pida. Para esto es necesario instalar el server
<a href="http://www.ejabberd.im/">Ejabberd</a> y configurarlo. Ademas de que es necesario habilitar MUCXEP-0045 y In-Band registration XEP-0077 en el servidor Ejabberd.

Es necesario contar con la librerias <a href="http://strophe.im/strophejs/">StropheJS</a> la cual ayudaran que el lado del cliente puedas cachar los mensajes XMPP.

<a href="https://github.com/misalabs/Frances"> Aqui esta un ejemplo</a> su funcionamiento es simple, el cliente se conecta al servidor Ejabberd, en este caso el StropheJS hace dicha tarea, despues en Python (Lado del server) cuando se quiera, se puede mandar un mensaje el cliente y listo, en este ejemplo cada que se introduce un dato a la BD se enviara un mensaje al cliente.

También dejo un <a href="http://youtu.be/VvMwi2fR0L0"> video</a>, ya saben, las imágenes dicen más que mil palabras.

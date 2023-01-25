---
title: Que es XMPP y BOSH ejabberd
date: 2013-01-13
---

XMPP es un protocolo con modelo de "cliente-servidor", actualmente en la Web no se soporta XMPP nativamente asi que el tráfico que se quiera realizar por XMPP se tendra que manejar dentro del cliente como Javascript/Flash etc. Ahora el problema más importante es como HTTP trabaja de manera unidireccional, es decir, el cliente manda un "request" y el server devuelve un "response" y la parte de hacerlo alreves se deja un lado osea que el server mande la información sin que se le pida. Y esto como para que?, pues ya anterioremente les habia platicado técnicas como polling, comet, long-polling las cuales estamos consultando si es que hay nueva información al servidor aumentando la latencía, imaginemos en Twitter como sin darle un reload a la página nos aparecen nuevos "Tweets", esto es gracias a que el servidor encontro nueva información e hizo un push para mandarnos esa nueva infromación.

XMPP es un protocolo libre, esto de los protocolos es simplemente la comunicación que se tiene entre maquinas, cuando las 2 instancias conocen el protocolo son capaces de entender y compartir información sin embargo cuando el protocolo es cerrado es muy dificil ver lo que quiere decir o lo que esta pasando. Actualmente hay varios protocolos cerrados, en mensajería instantanea imaginemos "MSN messenger", este protocolo de comunicación simplemente nadie lo entiende, solo hay algunos rudos quienes hicieron ingenieria inversa para entender el protocolo y asi crear clientes que puedan usarlo. Ahora un ejemplo con protocolo abierto de Gtalk de google que usa XMPP :)

XMPP trabaja a base de enviar XML, así también existen 3 elementos muy importantes que son el message, presence e iq. El message se trata del "mensaje" que enviaremos, presence es el "estado" del usuario como disponible, ausente blabla y iq se refiere a un id para enviarnos información necesaria.

En resumidas cuentas XMPP trabaja de manera persistente, es decir, la conexión esta disponible desde el principio hasta el final pudiendose transmitir todoso los datos que sean. En HTTP la conexión es de petición y respuesta, es decir, el cliente quiere algo y el servidor responde y puff hasta ahí.

Para implementar este tipo de metodología es necesario de un puente entre HTTP y XMPP y es ahi donde entra BOSH :-). BOSH se trata de eso, dejar abierto un canal el cual quede escuchando y si el servidor tiene algo que "decir" lo manda al cliente si no simplemente se queda ahi.

Existen diversos servidors los cuales se pueden usar, como ejabberd, tigase, openfire y jabber xcp. Aqui instalaremos ejabberd.

Esta instalación sera en un linux, ubuntu. Para instalarlo simplemente ponemos el comando.

```bash
$ sudo apt-get install ejabberd
```
Ahora paramos el servidor , esto para realizar algunas configuraciones

```bash
$ sudo /etc/init.d/ejabberd stop[/sourcecode]
```

Ahora editamos un archivo.

```bash
$ sudo gedit /etc/ejabberd/ejabberd.cfg
```

Y en la linea "%%Admin user" configurar el usuario y dominio que usaremos, en este caso le puse jabberdmisalabs.com , este dominio es el que usaremos para hacer las peticiones de manera local, es decir, tambien lo agregaremos en /etc/hosts quedando algo asi "127.0.0.1 jabbermisalabs.com www.jabbermisalabs.com"

<img class="center" src="/images/xmpp_1.png" />

Ahora lo iniciamos

```bash
$ sudo /etc/init.d/ejabberd start
```
Y finalmente configuramos el usuario con su password, sustitumos las "xxxx" por nuestra clave

```bash
$ sudo ejabberdctl register asim jabbermisalabs.com xxxxxx
```

Ahora vamos al navegador al http://jabbermisalabs.com:5280/admin introducimos como usuario algo asi como asim@jabbermisalabs.com y la clave la que habiamos especificado. Finalemente entramos al Admin.

<img class="center" src="/images/xmpp_2.png"/>

Existen muchas aplicaciones los cuales podemos realizar como chats, juegos en tiempo real, edición de documentos en tiempo real, etc. En un futuro ya pondre algunos ejemplos del potencial de este protocolo.

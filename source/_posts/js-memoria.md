---
title: ¿Cargar memoria en el cliente o en el servidor?
date: 2012-02-25
---

Un dia de mis ayeres me encontre con que tenia que realizar peticiones de datos a una BD mediante una web, el usuario tenia que registrar codigos de barras mediante un sistema web el cual ese código de barras se buscaba en la base de datos de un chingo de registros y al final cambiaba el estatus del codigo de barras como “Escaneado”.

Muy cabron si tenemos en cuenta que hay buscar el codigo de barras en una base de miles de miles de codigos de diferentes y ademas no es solo un tipo quien esta registrando, si no muchos monitos
atacando a la BD, osease el Servidor se sobrecargaba D:

![](/images/cliente-servidor-http.png)

Recordemos que se tienen al cliente y el servidor el cual nos responde dependiendo de nuestras solicitudes. Sin embargo con algo de Jquery podemos realizar las consulta de manera asincrona y que el usuario no se de ni cuenta de que ya se estan registrando. Se tenian dos soluciones implementadas algo “idiotas” por mi parte para esto:

En vivo cada que el codigo se registraba con JQuery y Javascript y blabla mandamos el codigo a un PHP el cual nos hacia el favor de buscarlo y cambiarle el estatus en la BD. Cargando asi al servidor de BD segundo a segundo.  .
En vivo cuando el usuario abria la ventana de “registro de codigos” se cargaban todos los datos en memoria del cliente usando algo de Javascript, ahora cuando se registraba el codigo consultabamos la tabla de Javascript ya cargada con anterioridad al final del registro mandamos los datos que guardamos en el cliente y se hace “una” sola consulta por asi decirlo. Cargando asi, “en parte”, solo la memoria del clientes. 
Ahora la gran interrogante de donde es mejor el manejo de una gran cantidad de datos, ¿en el servidor o en el cliente?. En el servidor se da por hecho que si son un chingo de usuarios se estaria atacando constantemente a la BD y en cuanto a cargar al cliente pues sacrificariamos memoria en el cliente, aun asi al terminar se haria una consulta a la BD pero ya es solo “una” consulta con varios codigos de barras.

Mucho blablabla ninguna de las 2 formas anteriores nos sirvio jojojo, alguna vez en mis noches de andar por la red de aqui de haya, de por acuya lei que es bueno el manejo de mucha informacion en txt planos la unica gran solucion que se pudo dar es no cargar ni en el servidor ni en el cliente  fuaaaaaaaaa.

Al registrar los codigos de barras lo hacemos en un TXT plano asi que registren todo lo que quieran, hasta el codigo de barras del bote de frutsi si quieren, el TXT los va ir registrando sin importar que codigo de barras sea {Solo estariamos sacrificando trafico en la red puesto que ese TXT se estara guardando dentro del servidor}. Ya al final cuando se le de “Guardar” o “Fianlizar” o “Ya termine tio” se agarra el TXT generado y vualaaaa empieza a hacer las busquedas y actualizacion de estatus que se encuentren.

Al final se estara atacando a la BD con los miles de codigos que tengamos en el TXT pero pues eso es otra historia canijos, programacion escalable, balanceo de cargas blabla.

Conclusión

Al final hay que tener un balanceo en ambas partes, tanto como en el cliente como en el servidor, con eso de JavaScript y JQuery abusamos de lo que nos ofrece y se tiende a cargar mucho al cliente. Tambien hay que mencionar que si queremos gran manejo de datos usemos TXT planos o un XML o ya de perdida JSON.

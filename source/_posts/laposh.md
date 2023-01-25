---
title: Laposh, conectando gente y liberación
date: 2013-07-06
---

Hace ya tiempo, un año o mas, tiempo estaba interesado en la elaboración de un sistema el cual te conectara con gente que no conoces  con tus gustos personales mediante un Chat y un camara. Era una especie de ChatRuleta pero la idea era agregar un algoritmo el cual te vaya juntando con gente de tus mismas preferencias.

Ya con mi idea y dando vueltas por aquí y por acuya entonces vi que en el lenguaje Python podría podria hacerlo. Así que después de investigar y demás llegue a la conclusión de que usaría Python Django y Tornado  :D. Entonces fue en este proyecto que decidí aprender Python :0.

Después de varios topes con <a href="http://www.tornadoweb.org/en/stable/">Tornado Web Server</a>pude integrarlo con Django y pues salio la primera versión :D en ese entonces y ahí se quedo ahahah en realidad mi gran problema era integrar las sesiones de Tornado con Django. Así que pufff termine deshaciéndome de Tornado y opte por usar otro tipo de tecnología asíncrona que es <a href="http://misalabs.com/2013/01/13/xmpp">XMPP</a>, el cual hablo en otros posts.

En realidad el proyecto sigue apagado por diversos aspectos, mas que nada el tiempo que se requiere de escupir lineas de código así que decidí que este proyecto liberarlo como Software libre para quien sea que este interesado en implementar alguna idea similar o para colaborar con el proyecto. En realidad la idea es ya no usar Tornado si no que usar XMPP y de ahí integrarlo con el Framework Django ;)

Bajo el sueño surrealista que tuve hace poco sobre andar buscando donde comerme un pollo que tenia en la mano la posible interpretación es que cargo y busco donde desarrollar algo, así que dejo libre el proyecto, en realidad ya tengo otras ideas en mente y como dicen "es mejor contradecirse todo el tiempo". En el Karma-Code para volver a llenar un vaso primero hay que vaciarlo.

El sitio esta alojado en <a href="http://heroku.com/">Heroku</a>, la URL es <a href="laposh.herokuapp.com">laposh.herokuapp.com</a> y se encuentra alojado en <a href="https://github.com/misalabs/laposh">Github</a>, si quieren correrlo  en local basta con bajarlo de Github y ejecutar en terminal:

```bash
$ python manage.py nucleo --reload 8000
```
Ir al browser en la URL http://127.0.0.1:8000

<img class="center" src="/images/laposh.png" />

Nota mental que nunca hice caso: El código esta algo indecente, eran otras épocas, apenas aprendía Python. Como cuando vez una foto de ti de hace tiempo y tu peinado te parece una locura...

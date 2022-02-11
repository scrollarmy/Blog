---
layout: post
title: Como publicar una web con presupuesto cero
subtitle: El paso a paso y herramientas que usamos para levantar nuestra web
comments: false
readtime: true
---

# Como publicar una web con presupuesto cero (o casi)
La idea del post es mostrar como generar una web estatica con un presupuesto minimo utilizando cloudflare como dns y github haciendo de hosting. Con esto vamos a poder tener administrar subdominios (*en un proximo post*) y también generar cambios en la web simplemente pusheando a master, un CD para el pueblo casi.

![Let's see your budget](https://media0.giphy.com/media/QAh4fa5BD95ZZKb372/giphy.gif?cid=ecf05e47b52g98vg2x8jj9430g7pisbkppcobjq6t4vee24f&rid=giphy.gif&ct=g){: .mx-auto.d-block :}


Vamos a sumar un dominio .com.ar que a fecha de hoy vale $475 ARS el registro anual, unos 2.37 USD Blue, en caso de no comprar el dominio Github nos da uno del formato `https://usuario.github.io` pero perdemos la chance de sumar subdominios y seguir metiendo cosas a nuestra web principal ya que podemos meter un blog, una pagina de status de servicios o cualquier cosa que podamos meterle que no requiera un server complejo y pueda hacerse mediante github actions o similar.

---

## Puesta en marcha

1. Configurar sitio en cloudflare
    1. En el panel principal vamos a ir a `Sitios` y presionamos en `add`
    2. Vamos a agregar 2 registros CNAME apuntando al repositorio
        `CNAME  www usuario.github.io`

        `CNAME  <dominio>.com.ar   usuario.github.io`

        ![CloudFlare config](https://i.imgur.com/8F6p76V.png)
    3. Guardamos los nombres de los servidores que tendremos que delegar en el paso siguiente
    
        `addilyn.ns.cloudflare.com`

        `bruce.ns.cloudflare.com`
    
    4. Despues vamos la sección de SSL/TLS, configuramos el modo de encriptación como Full y también activamos las recomendaciones de SSL/TLS

    ![CloudFlare config](https://i.imgur.com/bLQtqjV.png)

2. Comprar y delegar el domino
    1. Una vez adentro del TAD nos vamos a "delegaciones NIC" y seleccionamos delegar al dominio deseado
    ![TAD NIC config](https://i.imgur.com/8Hfjza8.png)
    ![TAD NIC config](https://i.imgur.com/QaYPGYf.png)
    Luego de guardar todo puede demorar hasta 30min hasta verse reflejado el cambio

3. Mientras que esperamos que se apliquen los cambios vamos a <del>robar<del> hacer nuestra y subirla a la branch main de nuestro repo

    La web de Scrollarmy se basa en la template de **Inovatik**. Acá el [Link de descarga](https://www.behance.net/gallery/81106457/Leno-Free-Mobile-App-Landing-Page-HTML-Template)

    Modificando el css y cargando nuestra info pasamos de esto
    ![Template Original](https://i.imgur.com/qUcWevV.png)
    a esto
    ![Sitio actual](https://i.imgur.com/mNIOobD.png)

    Ya con el sitio a gusto lo subimos al repo.
    
4. Configurar git pages:
    
    Esto `solo se hace cuando se tiene un dominio personalizado` y no los que entrega Github por defecto
    
    Vamos a ir a la configuración del repositorio donde tenemos nuestra web y luego a la seccion pages
    
    Por defecto la rama master esta seleccionada y nosotros vamos a configurar los siguientes puntos
    ![Github pages](https://i.imgur.com/irg5TKy.png)

    - Custom domain: 
    colocaremos nuestro dominio, que compramos previamente
    
    - Deshabilitar trafico seguro, esto lo hacemos ya que desde cloudflare estamos controlando esta feature.

## ¿Con que seguimos?

Con estos pasos ya tenes tu web alojada en github con https todo gratuito o por muy bajo costo, administrado en conjunto con cloudflare lo que nos va a permitir generar subdominios con la misma metodologia, subiendo nuestros archivos a un repositorio nuevo, esto lo vamos a ver en otra entrada del blog. 
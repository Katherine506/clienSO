---
title: "Configuración de la página web"
date: 2025-04-04
weight: 7
---

Configuración de la página web

<!--more-->

## Configuración de la página web

Para iniciar vamos a crear un sitio web. Debemos primero borrar la página default para poder hacer la nuestra, lo cual los archivos HTML y CSS estarán en la carpeta `wwwroot`.  
Nuestra página se llamará **www.clienso.com**.

**Nota:** Debemos tener acceso a una carpeta de nuestra computadora (como una carpeta compartida en el virtualizador) para pasarnos los archivos que necesitemos y poder tener en nuestro servidor el archivo HTML y CSS de nuestra página web.

**Figura 43**: Enlace de carpeta ShareVM.
![Figura 43](../images/43.png)

Para agregar el sitio web lo haremos de la siguiente manera:  
Nombre del sitio: **Clienso**, carpeta: **wwwroot** y la dirección IP será la de nuestro servidor. Luego le damos **Aceptar**.

**Figura 44**: Configuración de la página web en el servicio IIS.
![Figura 44](../images/44.png)

Una vez hagamos esto, iremos a la configuración del **DNS** para poder agregar una **zona nueva** que nos permita tener el host de nuestra página web.

**Figura 45**: Creación de la zona nueva en el DNS.
![Figura 45](../images/45.png)

Pasos:

- Seleccionamos _zona nueva_
- Clic en _Siguiente_
- Seleccionamos _zona principal_
- Aplicable a todos los servidores DNS que se ejecutan en el dominio
- Nombre de zona: `clienso.com`
- Seleccionamos _permitir solo actualizaciones dinámicas seguras_
- Finalizar

Una vez sigamos estos pasos, estará terminada nuestra zona segura en el DNS para la página web.

**Figura 46**: Pantalla de finalización de la zona creada.
![Figura 46](../images/46.png)

Una vez finalizado esto, ingresamos a la zona creada. Dentro de ella damos doble clic y seleccionamos la opción **Host nuevo**.

**Figura 47**: Imagen de la prueba de host nuevo.
![Figura 47](../images/47.png)

Para la configuración del host ponemos el dominio: **www** y la dirección IP de nuestro servidor, que sería `192.168.0.1`.

**Figura 48**: Imagen del host creado.
![Figura 48](../images/48.png)

Una vez creado el host, lo que haremos es que dentro de los enlaces de nuestra página web vamos a poner que nuestro host será **www.clienso.com** y la IP de nuestro servidor, para que se vea de esta manera:

![Figura 49](../images/49.png)

También debemos agregar nuestro enlace con el **HTTPS** para que sea un sitio web seguro.  
Seleccionamos **Agregar** y usamos la siguiente configuración en IIS:

- Puerto: 443
- Tipo: https
- Certificado: el generado anteriormente
  ![Figura 50](../images/50.png)

Para no tener problemas con la página siendo segura o no. Vamos a tener que crear una regla para detectar la dirección HTTP a HTTPS. En nuestra página principal de CENSISOPER seleccionamos reescritura del URL para crear una regla para el enlace, que debe verse lo siguiente:

![Figura 51](../images/51.png)

![Figura 52](../images/52.png)

Con esto creado, ya vamos a poder acceder a la página con el enlace **clienso.com** y siempre nos estará direccionando automáticamente al enlace **HTTPS**, reemplazando cualquier acceso por `http`.

---

<div style="text-align: center; margin-top: 3rem;">
  <a href="/_index.md" style="
    display: inline-block;
    background-color: #ff9800;
    color: white;
    padding: 10px 20px;
    border-radius: 8px;
    text-decoration: none;
    font-weight: bold;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    transition: background-color 0.2s ease;">
    ← Volver al inicio
  </a>
</div>

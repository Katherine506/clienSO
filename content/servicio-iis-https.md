---
title: "IIS y HTTPS"
date: 2025-04-04
weight: 4
---

Creación del servicio IIS y enlace HTTPS

<!--more-->

## Creación del servicio IIS y enlace HTTPS

Para la creación de nuestro servicio web, debemos agregar nuevas características al servidor:

- Servidor web (IIS)
- Servicios de certificados de Active Directory

Esto nos permitirá montar un sitio web seguro con soporte para **HTTPS**. Instalaremos estos servicios como lo hicimos con **DHCP** y **DNS**.

Para ambos servicios no agregaremos características adicionales. En el caso de **IIS**, no se añaden más roles, y para **Certificate Authority** se deja únicamente la **entidad de certificación**.

Una vez instalado el Certificate Authority, se solicitarán las credenciales, que dejaremos como `CLIENSO/Administrador`.

En la configuración:

- Rol: Entidad de certificación
- Tipo de instalación: CA empresarial (ya que estamos en un dominio)
- Tipo de CA: Raíz
- Generamos una nueva clave privada
- Algoritmo: `SHA256`
- Longitud de clave: `2048`
- Nombre de CA: `clienso-CENSISOPER-CA`
- Validez: **5 años**

Al final, confirmamos la información.

**Figura 40**: Confirmación de la instalación del Certificate Authority.
![Figura 40](../images/40.png)

Luego aparecerá la confirmación de la CA, y hacemos clic en **Configurar** para terminar la instalación.

---

## Instalación del módulo URL Rewrite

Una vez instalados los roles, necesitaremos conectarnos a internet para instalar el módulo **URL Rewrite** para IIS.

Descargamos la versión en español (x64) desde la web oficial.

**Figura 41**: Imagen de la página para la instalación del módulo URL Rewrite.
![Figura 41](../images/41.png)

Una vez descargado, ejecutamos el instalador desde la carpeta de descargas.

**Nota:** Para conectarse a internet, se recomienda:

- Desactivar temporalmente la IP estática del servidor
- Cambiar a adaptador puente
- Luego de la instalación, volver a configurar la IP estática y la red interna en el virtualizador

**Figura 42**: Verificación de la instalación del URL Rewrite.
![Figura 42](../images/42.png)

---

<div style="text-align: center; margin-top: 3rem;">
  <a href="https://katherine506.github.io/clienSO/" style="
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

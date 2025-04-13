---
title: "DHCP"
date: 2025-04-04
weight: 3
---

Configuración del DHCP

<!--more-->

## Configuración del DHCP

Una vez creado nuestro AD necesitamos configurar nuestro DHCP, para esto vamos a abrir una consola de Powershell con permisos de administrador. Antes, vamos en consola a poner el comando `Get-NetIPConfiguration` para saber a qué IP estamos conectados, nos debería salir de la siguiente manera.

**Figura 28**: Corroboración de IP.
![Figura 28](../images/28.png)

Una vez corroboramos que estemos en la IP correcta, vamos a usar el comando `Get-WindowsFeature -Name *dhcp*`, esto para verificar que no esté instalado este servicio antes, si no lo está, aparecería de la siguiente manera.

**Figura 29**: Verificación de DHCP instalado.
![Figura 29](../images/29.png)

Luego de esto usaremos el comando `Install-WindowsFeature -Name dhcp` para empezar la instalación del mismo, debemos esperar a que termine de cargar.

**Figura 30**: Instalación DHCP.
![Figura 30](../images/30.png)

Una vez terminada la instalación, lo corroboramos con el comando `Get-WindowsFeature -Name *dhcp*`, nos aparecerá de la siguiente manera.

**Figura 31**: Corroboración con el comando Get-WindowsFeature -Name _dhcp_.
![Figura 31](../images/31.png)

Acto siguiente vamos a instalar las herramientas del DHCP con el comando `Install-WindowsFeature -Name dhcp -IncludeManagementTools`

**Figura 32**: Instalación de las herramientas del DHCP.
![Figura 32](../images/32.png)

Una vez terminada la instalación, lo corroboramos con el comando `Get-WindowsFeature -Name *dhcp*`, nos aparecerá de la siguiente manera.

**Figura 33**: Corroboración de la instalación de DHCP.
![Figura 33](../images/33.png)

Cuando tengamos instaladas ambas funciones vamos a empezar configurando el DHCP, empezaremos poniendo el siguiente comando:  
`Add-DhcpServerInDC -DnsName clienso.org -IPAddress 192.168.0.1`  
Debemos poner el nombre del dominio que creamos junto con su dirección IP y le damos enter.

**Figura 34**: configuración de DHCP.
![Figura 344](../images/34.png)

Si queremos verificar que se instaló el DHCP corremos el comando `Get-DhcpServerInDC` y nos mostrará el nombre de la DNS con su IP.

**Figura 35**: Verificación de instalación DHCP.
![Figura 35](../images/35.png)

Luego de esto debemos agregar la seguridad de grupo con el comando `Add-DhcpServerSecurityGroup`.

Después de esto vamos a configurar el rango de IPs donde se pueden conectar los clientes. Deben tener en cuenta que existen ciertas IPs reservadas, así que recomendamos usar la 192.168.0.20 hasta la 192.168.0.200. El comando completo sería:  
`Add-DhcpServerv4Scope -Name "Rango DHCP" -StartRange 192.168.0.20 -EndRange 192.168.0.200 -SubnetMask 255.255.255.0`

Si queremos corroborar que se instaló correctamente usamos el comando `Get-DhcpServerv4Scope`.

**Figura 36**: Verificación de instalación.
![Figura 36](../images/36.png)

Para activar el DHCP en las computadoras debemos usar el siguiente comando:  
`Set-DhcpServer4OptionValue -DnsServer 192.168.0.1 -Router 192.168.0.1`  
Y con esto ya tenemos configurado el DHCP.

**Figura 37**: Activación de DHCP.
![Figura 37](../images/37.png)

Una vez finalizado, veremos que tenemos un símbolo de warning en la bandera al lado de **Administrar** en la configuración del servidor. Le damos a **Completar configuración de DHCP**, luego a **Siguiente** y al final a **Confirmar** para terminar la configuración. Y con eso terminamos de configurar el DHCP.

**Nota:** Recomendamos luego de terminar la instalación reiniciar el sistema.

**Figura 38**: Aviso de configuración DHCP.
![Figura 38](../images/38.png)

**Figura 39**: Autorización posterior a la instalación de DHCP.
![Figura 39](../images/39.png)

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

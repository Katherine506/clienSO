---
title: "Active Directory y DNS"
weight: 5
---

Instalación del Active Directory y DNS

<!--more-->

## Creación del Active Directory

Antes de realizar la instalación del **Active Directory**, como recomendación inicial debemos:

- Establecer la dirección IP del servidor.
- Esto facilitará la conexión de los clientes al dominio.
- Ir a la configuración de red y asignar una IP fija al servidor.

**Figura 12**: Selección de dirección IP del servidor, parte uno.
![Figura 12](https://katherine506.github.io/clienSO/images/12.png)

**Figura 13**: Selección de dirección IP del servidor, parte dos.
![Figura 13](../images/13.png)

**Figura 14**: Selección de dirección IP del servidor, parte tres.
![Figura 14](../images/14.png)

> 💡 Entramos a la configuración de IPv4 y asignamos una dirección IP manualmente. Opcionalmente, podemos deshabilitar IPv6.

---

### Agregar roles y características

- Desde el panel principal seleccionamos: **“Agregar roles y características”**.

**Figura 15**: Configuración de servidor local.
![Figura 15](../images/15.png)

**Figura 16**: Agregar roles y características.
![Figura 16](../images/16.png)

- Elegimos **“Instalación basada en características o en roles”**.

**Figura 17**: Selección de tipo de instalación.
![Figura 17](../images/17.png)

- En la selección de servidor, seleccionamos el servidor creado (`CenSisOper`).

**Figura 18**: Selección de servidor de destino.
![Figura 18](../images/18.png)

> 📝 _Podés cambiar el nombre del servidor desde el panel, pero requerirá reiniciar la VM._

---

### Selección del rol de Active Directory

- En la sección de roles, seleccionamos **“Servicios de dominio de Active Directory”**.
- Hugo nos preguntará si queremos agregar características necesarias → elegimos **“Agregar características”**.

**Figura 19**: Selección de rol.
![Figura 19](../images/19.png)

**Figura 20**: Agregar características necesarias.
![Figura 20](../images/20.png)

- Continuamos haciendo clic en **“Siguiente”** hasta llegar a la sección de confirmación.
- Marcamos la opción de **reiniciar automáticamente el servidor después de instalar**.
- Hacemos clic en **“Instalar”**.

**Figura 21**: Confirmación de selecciones de instalación.
![Figura 21](../images/21.png)

---

### Promover el servidor a controlador de dominio

- Una vez terminada la instalación, hacemos clic en **“Promover este servidor a controlador de dominio”**.

**Figura 22**: Progreso de instalación.
![Figura 22](../images/22.png)

- En la opción de implementación elegimos:  
  → **“Agregar un nuevo bosque”**  
  → Dominio: `clienso.org`

**Figura 23**: Configuración de implementación.
![Figura 23](../images/23.png)

---

### Configuración del controlador de dominio

- Nivel funcional del dominio: `Windows Server 2025`
- Asignamos una contraseña segura para el dominio.
- Continuamos con los pasos siguientes.

**Figura 24**: Opciones del controlador de dominio.
![Figura 24](../images/24.png)

- En las opciones adicionales, dejamos el nombre NetBIOS como `CLIENSO`.

**Figura 25**: Opciones adicionales.
![Figura 25](../images/25.png)

---

### Finalizar la instalación

- Podemos revisar todas las configuraciones seleccionadas.
- Si todo está correcto, hacemos clic en **“Instalar”**.
- Al finalizar, la máquina se reiniciará automáticamente.

**Figura 26**: Revisión final.
![Figura 26](../images/26.png)

**Figura 27**: Comprobación de requisitos previos.
![Figura 27](../images/27.png)

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

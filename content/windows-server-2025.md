---
title: "Windows Server 2025"
weight: 2
---

Instalación de Windows Server 2025

<!--more-->

## Instalación de Windows Server

Para la instalación de nuestro sistema operativo, vamos a seleccionar primero nuestro virtualizador de preferencia, en este caso Oracle Virtual Box. Y el sistema operativo que vamos a instalar para el manejo del servidor será **Windows Server, versión 2025**.

---

### 1. Ruta de instalación y hardware del virtualizador

Una vez iniciada la máquina virtual:

- Le asignamos un nombre.
- Escogemos la ruta de instalación de preferencia.
- Seleccionamos la imagen `.iso` del sistema operativo.
- Seleccionamos **"Omitir instalación desatendida"** para mayor control de recursos.

**Figura 1**: Instalación de la máquina virtual.  
![Figura 1](../images/1.png)

Luego, configuramos:

- Memoria RAM.
- Procesadores del CPU.
- Almacenamiento asignado.

**Figura 2**: Selección de hardware de la máquina virtual.  
![Figura 2](../images/2.png)
**Figura 3**: Selección de tamaño de disco duro de la máquina virtual.
![Figura 3](../images/3.png)

Con esto, montamos la máquina virtual y solo quedaría reiniciarla para iniciar la instalación del sistema operativo Windows Server.

---

### 2. Opciones de instalación de Windows Server

Después de configurar la máquina virtual, iniciamos la instalación. El asistente nos pedirá:

- Selección del idioma y zona horaria.

**Figura 4**: Configuración de idioma de la máquina virtual.
![Figura 4](../images/4.png)  
**Figura 5**: Configuración de teclado de la máquina virtual.
![Figura 5](../images/5.png)

A continuación, seleccionamos:

- **"Instalar Windows Server"**.
- Aceptamos la advertencia de que los datos serán eliminados.

**Figura 6**: Selección de opción de configuración.
![Figura 6](../images/6.png)
Seleccionamos la versión:

- `Windows Server 2025 Standard Evaluation (experiencia de escritorio)`

**Figura 7**: Selección de imagen de Windows Server.
![Figura 7](../images/7.png)

Aceptamos los **términos de licencia** y seleccionamos el disco donde instalar.

> 💡 _Tip: Podés crear particiones si querés dividir el almacenamiento._

**Figura 8**: Selección de ubicación para instalar Windows Server.
![Figura 8](../images/8.png)

Finalmente, pulsamos **"Instalar"** y comienza el proceso.

**Figura 9**: Instalación de Windows Server.  
![Figura 9](../images/9.png)

**Figura 10**: Inicio automático tras reinicio.
![Figura 10](../images/10.png)

Creamos una contraseña para el usuario y el sistema estará listo para iniciar sesión.

**Figura 11**: Personalización del sistema operativo.
![Figura 11](../images/11.png)

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

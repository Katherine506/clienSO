---
title: "Políticas de grupo"
date: 2025-04-04
---

Configuraciones GPO

<!--more-->

**1. Cambiar fondo de pantalla por uno que la empresa decida**

Guarda FondoEmpresarial.jpg en un recurso compartido accesible e.g (\servidor\fondos).

Crea una nueva GPO llamada “FondoPantallaCorporativo” y dale **click derecho > Editar**

![Figura 72](../images/72.png)

Luego ve a Configuración de usuario **> Plantillas administrativas> Active Desktop** y da clic en Active Desktop.

![Figura 73](../images/73.png)

Habilita las configuraciones de Habilitar Active Desktop, No permitir cambios y Tapiz del escritorio

![Figura 74](../images/74.png)

Ve a la carpeta compartida, la cual debe tener todos los accesos compartidos habilitados, y copiar la ruta de la imagen en formato JPG.

Agrega la ruta de la imagen en Nombre del papel tapiz, en la configuración de Tapiz del escritorio que habilitamos en el punto anterior, luego elige el estilo de papel tapiz en rellenar, da aplicar y luego aceptar.

![Figura 75](../images/75.png)

Abre la consola y corre el comando:

`gpupdate /force`

**2. Deshabilitar el acceso al panel de control para los usuarios que no son de TI**

Crea nueva directiva llamada “Panel de Control”.
![Figura 76](../images/76.png)

Da click derecho **> Editar**

Navega hasta: **Configuración de usuario > Plantillas administrativas > Panel de control.**

Busca y haz doble clic en: “Prohibir el acceso al Panel de control y a la configuración de PC”.

![Figura 77](../images/77.png)

Selecciona Habilitada y haz clic en Aceptar.

![Figura 78](../images/78.png)

Ahora, ve a aplicar la política solo a los usuarios que NO son de TI.

En Ámbito ve a Filtrado de seguridad, se dejan los grupos a los que le quiero aplicar la directiva.

![Figura 79](../images/79.png)

En delegación, agrega a Usuarios autenticados con permiso de lectura.

![Figura 80](../images/80.png)

![Figura 81](../images/81.png)

Luego agrega al grupo de TI le permito leer y le doy “Denegar” a Aplicar directiva de grupo.

Agregar el grupo TI y marca la opción Denegar en Aplicar la directiva de grupo.

![Figura 82](../images/82.png)

![Figura 83](../images/83.png)

![Figura 84](../images/84.png)

Da “Aplicar” y “Aceptar”.

Abre la consola y corre el comando:

`gpupdate /force`

**3. Definir cómo página inicial del Internet Explorer el sitio del sitio web**

Crea una nueva GPO llamada “PaginaInicioExplorer” da click derecho editar

![Figura 86](../images/86.png)

Ve a **Configuración de usuario > Plantillas administrativas > Componentes de Windows y da click en Internet Explorer**.

Busca la configuración de “Deshabilitar en cambio de configuración de la página principal” habilitala.

Pon en la opción de la página principal la URL del sitio web que desea, da aplicar y aceptar.

![Figura 87](../images/87.png)

Abre la consola y corre el comando:

`gpupdate /force`

**4. Deshabilitar la ejecución de los ejecutables: notepad.exe y regedit.exe.**

Crea una nueva GPO con el nombre “DesactivarEjecEjecutables”
Haz clic derecho en la GPO que has creado y selecciona Editar.

![Figura 88](../images/88.png)

En el Editor de administración de directivas de grupo, navega a **Configuración de Usuario > Directivas> Configuración de Windows > Configuración de Seguridad > Directivas de restricción de software**

![Figura 89](../images/89.png)

En Directivas de restricción de software, haz clic derecho en **"Restricciones de Software" y selecciona "Nuevas directivas de restricción de software" > "Reglas adicionales"**.

Haz clic derecho en "Reglas adicionales" y selecciona "Regla de nueva ruta de acceso..".

![Figura 90](../images/90.png)

Ruta: Especifica el camino completo del archivo ejecutable a bloquear:

Para notepad.exe: **C:\Windows\System32\notepad.exe**

Para regedit.exe: **C:\Windows\regedit.exe**

Selecciona **"No permitido"**. Luego de **Aplicar y Aceptar**.

![Figura 91](../images/91.png)

![Figura 92](../images/92.png)

Abre la consola y corre el comando

`gpupdate /force`

**5. Renombrar Usuarios Administrador y Temporal**

Paso 1. Crear una GPO para renombrar los usuarios deseados

![Figura 93](../images/93.png)

En la herramienta “Administración de directivas de grupo” clic derecho sobre “clienso.org” y clic en “Crear un GPO en este dominio y vincularlo aquí…”

![Figura 94](../images/94.png)

En nombre escriba **RenombrarUsuarios** y clic en **Aceptar**

Ahora haga clic derecho sobre la nueva GPO y clic en **Editar**

Vaya a **Configuración del equipo > Directivas > Configuración de Windows > Configuración de seguridad > Directivas locales > Opciones de seguridad**.

En la lista de la ventana derecha busque **Cuentas: estado de la cuenta de administrador**, clic derecho y **Propiedades**.

![Figura 95](../images/95.png)

En la ventana emergente marque la casilla **Definir esta configuración de directiva:** y clic en **Habilitada**.

Clic en **Aplicar y Aceptar**

De vuelta en la lista de **Opciones de seguridad** busque **Cuentas: estado de la cuenta de invitado**.

Clic derecho y **Propiedades** En la ventana emergente marque la casilla **Definir esta configuración de directiva:** y clic en “Habilitada”. Clic en **Aplicar y Aceptar**.

De vuelta en la lista de **Opciones de seguridad** busque **Cuentas: cambiar el nombre de la cuenta de administrador** y marque la casilla **Definir esta configuración de directiva** ahora escriba **usrmda**

![Figura 96](../images/96.png)

Clic en **Aplicar y Aceptar**

Hacer lo mismo con **Cuentas: cambiar el nombre de la cuenta de invitado** y marque la casilla **Definir esta configuración de directiva** ahora escriba **usrtmp**

![Figura 97](../images/97.png)

¡Listo!

**6. Carpetas personales en DFS**

**Paso 1**. Montar una nueva unidad de disco duro en la máquina virtual de servidor

![Figura 98](../images/98.png)

**Paso 2**. Montar el nuevo disco en el servidor, con la herramienta **Crear y formatear particiones del disco duro**

![Figura 99](../images/99.png)

Al ingresar por primera vez luego de montar una unidad se abre una ventana emergente, se debe inicializar el disco clicando en **Aceptar**

![Figura 100](../images/100.png)

Clic derecho sobre el nuevo disco y clic en **Nuevo volumen simple…**

![Figura 101](../images/101.png)

Seguir las indicaciones del asistente para nuevo volumen. Al inicio “Siguiente” En especificar el tamaño del volumen dejar el tamaño total y clic en “Siguiente”

![Figura 102](../images/102.png)

Asignar la letra “P” a la unidad y “Siguiente”

![Figura 103](../images/103.png)

En Formatear la partición, dejar los valores por defecto y “Siguiente”

![Figura 104](../images/104.png)

Clic en “Finalizar”. Debería ver la nueva unidad de disco duro asignada a la letra P

**Paso 3**. Crear la carpeta compartida para albergar las subcarpetas personales Ir a la unidad P: y crear una nueva carpeta llamada “Personal”

![Figura 105](../images/105.png)

Clic derecho sobre la carpeta, “Propiedades”, ir a la pestaña “Compartir”, clic sobre “Compartir…”

![Figura 106](../images/106.png)

Sobre la barra de búsqueda, busque y agregue los grupos de seguridad “SYSTEM” y “Admins. del dominio” y clic en “Compartir” y luego en “Listo”

![Figura 107](../images/107.png)

Vaya a la pestaña “Seguridad”, clic en “Opciones avanzadas”

![Figura 108](../images/108.png)

Clic “Agregar”

![Figura 109](../images/109.png)

Clic “Seleccionar una entidad de seguridad”

![Figura 110](../images/110.png)

Buscar y seleccionar el grupo de seguridad “Usuarios autentificados” y asignar permisos de “Lectura y ejecución” y “Mostrar contenido de la carpeta” y clic en “Aceptar”

![Figura 111](../images/111.png)

Clic en “Aplicar” y “Aceptar”

![Figura 112](../images/112.png)

**Paso 4**. Crear un nuevo recurso compartido con DFS para la carpeta personal.

En la herramienta “Administrador del servidor” vaya a “Herramientas”, luego “Administración de DFS”

![Figura 113](../images/113.png)

Clic en “Nuevo espacio de nombres”

![Figura 114](../images/114.png)

En “Servidor” escriba “CENSISOPER.clienso.org” y clic en “Siguiente”

![Figura 115](../images/115.png)

En “Nombre” escriba “Personal” y clic en “Siguiente”, en la ventana emergente de advertencia clic en “Sí”

![Figura 116](../images/116.png)

En “Tipo de espacio de nombres” dejar como por defecto y clic en “Siguiente” En “Revisar la configuración…” clic en “Crear” y al finalizar clic en “Cerrar”

Ahora debe crear una carpeta dentro del espacio de nombres “Personal”. Clic derecho sobre el DFS “Personal”, clic en “Nueva carpeta”

![Figura 117](../images/117.png)

En “Nombre” escriba “Usuarios” y clic en “Agregar”

![Figura 118](../images/118.png)

En “Ruta de acceso de destino de carpeta” escriba “\CENSISOPER.clienso.org\Personal” y clic en “Aceptar" y clic en “Aceptar” de nuevo

![Figura 119](../images/119.png)

**Paso 5**. Crear la política de grupo para la asignación automática a cada usuario.

En “Administrador del servidor” vaya a “Administración de directivas de grupo”

![Figura 120](../images/120.png)

Haga clic derecho sobre “clienso.org” y clic en “Crear un GPO en este dominio y vincularlo aquí…”

![Figura 121](../images/121.png)

En nombre escriba **CarpetasPersonalesDFS** y clic en “Aceptar” Haga clic derecho sobre la GPO “CarpetasPersonalesDFS” y clic “Editar” Ir a **Configuración de usuario > Preferencias > Configuración de Windows > Asignaciones de unidades”, haga clic derecho sobre “Asignaciones de unidades**, clic “Nuevo”, clic “Unidad asignada”

![Figura 122](../images/122.png)

En la ventana emergente, en la pestaña “General” asegure la siguiente configuración:

**· Acción: `Crear`**

**· Marcar `Reconectar`**

**· Ubicación: `\CENSISOPER.clienso.org\Personal\Usuarios%username%`**

**· Letra de unidad: P: `Clic en “Aplicar” y “Aceptar”`**

![Figura 123](../images/123.png)

Ahora debe crear una Tarea Programada para que la GPO asigne a cada nuevo usuario su propia carpeta personal.

En el “Editor de administración de directivas de grupo” vaya a “Configuración de usuario > Preferencias > Panel de control > Tareas programadas”, clic derecho sobre “Tareas programadas”, clic “Nuevo”, clic.

![Figura 124](../images/124.png)

Asegure la siguiente configuración:

**Pestaña General**

**Nombre:** "Establecer permisos de carpeta personal"

**Descripción:** "Configura permisos exclusivos para la carpeta personal del usuario"

**Cuenta de usuario:** Seleccione "NT AUTHORITY\System"

**Marque** "Ejecutar con los máximos privilegios"

**Marque** “Oculto”

**Seleccione** "Configurar para Windows 7"

![Figura 125](../images/125.png)

**Pestaña Desencadenadores**

**Haga clic en** Nuevo

**Establezca** "Al iniciar sesión"

Asegúrese de que está configurado para "Usuario"

![Figura 126](../images/126.png)

**Pestaña Acciones**

**Haga clic en** “Nuevo”

**Acción:** "Iniciar un programa"

**Programa o script:** powershell.exe

**Agregar argumentos:**
-NoProfile -ExecutionPolicy Bypass -Command "Try { $folder = '\clienso.org\Personal\Usuarios' + $env:USERNAME; if (!(Test-Path $folder)) { New-Item -Path $folder -ItemType Directory }; icacls $folder /grant ('clienso' + $env:USERNAME + ':(OI)(CI)(F)') /inheritance:r } Catch { $\_.Exception.Message | Out-File 'C:\GPO_Permissions_Error.log' -Append }"

![Figura 127](../images/127.png)

Aún en el “Editor de administración de directivas de grupo”, vaya a:

**Configuración del Equipo > Directivas > Configuración de Windows > Configuración de seguridad > Directivas locales > Asignación de derechos de usuario**.

En la lista de la derecha busque “Iniciar sesión como proceso por lotes” y dar clic derecho sobre él y clic en “Propiedades”.

![Figura 128](../images/128.png)

En la ventana emergente marque “Definir esta configuración de directiva” y clic en “Agregar usuario o grupo…”, escriba **NT AUTHORITY\System**, clic en “Aceptar”

![Figura 129](../images/129.png)

De vuelta en el “Administrador de directivas de grupo” seleccione la GPO “CarpetasPersonalesDFS”, en la pestaña “Delegación”, agregue los grupos de seguridad de cada departamento

![Figura 130](../images/130.png)

¡Listo!

**7. Folder redirection**

Para poder tener re direction de lo que viene siendo de nuestros archivos en ‘Documentos’ a un espacio de memoria de red necesitaremos los siguientes requisitos:

Primeramente necesitaremos en nuestros recursos compartidos en nuestro disco D:/ vamos a crear un folder llamado ‘Folder Redirection o del nombre que nos parezca mejor.

![Figura 131](../images/131.png)

Al ir a recursos compartidos crearemos un nuevo recurso de perfil de recurso SMB - Rápido , en lo que es la ubicación debe ser la carpeta que creamos, y en el nombre del recurso lo que haremos será poner el nombre de la carpeta, pero con el signo de dólar el final de la misma. la cual quedaría así.

![Figura 132](../images/132.png)

En términos de permisos deben de quedar de la siguiente manera:

![Figura 133](../images/133.png)

En configuraciones seleccionamos: **Habilitar enumeración basada en el acceso y permitir almacenamiento en caché del recurso compartido.**

Aceptamos y continuamos con la instalación.

Al crear esta recuerden en nombre del recurso compartido, guardar esta dirección que la usaremos más adelante.

![Figura 134](../images/134.png)

Una vez finalizado esto, iremos a nuestras políticas de grupo y crearemos una llamada Folder Redirection.

Al tener creada la directiva de grupo, le damos **editar > Configuración de usuario > Directivas > Configuración de Windows -> Redirección de carpetas > Documentos de damos propiedades**.

Dentro de esta nos preguntará por una ruta de acceso a la, la cual pondremos la ruta que habíamos guardado anteriormente.

Y en configuración, seleccionamos la opción que dice ‘Mover el contenido de Documentos a la nueva ubicación’.

En destino la configuración es básica.

![Figura 135](../images/135.png)

![Figura 136](../images/136.png)

Para finalizar, iremos a la administración del DFS y debemos crear un espacio para el folder redirection.

Así que debemos ir a la administración del DFS y cerrar un espacio de nombre, el cual llamaremos redirection.

Dentro de esta creamos una carpeta llamada Mis Documentos por ejemplo. Se vería así.

![Figura 137](../images/137.png)

Una Vez creada esta, iremos a nuestra política de grupo

**editar -> configuración de usuario > Preferencias > Configuración de Windows > Asignación de unidades** e iremos a crear una unidad Acción debe ser **reemplazar > ubicación debe ser del espacio del DFS > Opción de reconectar** y la etiquetamos como redirection y debe de quedar de la siguiente manera. Con esto crearemos el folder redirection.

![Figura 138](../images/138.png)

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

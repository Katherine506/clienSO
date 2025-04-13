---
title: "Carpetas Compartidas y Cuotas"
date: 2025-04-04
---

Configuración de las carpetas compartidas y sus cuotas

<!--more-->

## Carpetas compartidas por departamentos

Antes de crear las carpetas compartidas por departamentos, creamos una partición D con el nombre Carpetas compartidas y le asignamos un espacio de 10GB. Esto se realiza con el objetivo de almacenar las carpetas compartidas en dicha partición, tal como lo solicita el enunciado. Ahora, continuamos con la creación de las carpetas compartidas.

En el panel derecho, nos dirigimos a Servicios de archivos y de almacenamiento > Recursos compartidos y hacemos clic derecho en "Nuevo recurso compartido...".

Dejamos el perfil de recurso compartido de archivos en "Recurso compartido SMB - Rápido" y seleccionamos Siguiente. En la sección Ubicación del recurso compartido, marcamos "Seleccione por volumen" y seleccionamos la partición D: tal como lo solicita el enunciado.

![Figura 53](../images/53.png)

Seleccionamos Siguiente y, en Nombre del recurso compartido, ponemos el nombre del departamento correspondiente, en este caso “Contabilidad”. En la descripción, escribimos “Carpeta destinada al departamento de contabilidad” y, seguidamente, seleccionamos Siguiente.

![Figura 54](../images/54.png)

En la siguiente pantalla, marcamos Habilitar enumeración basada en el acceso y hacemos clic en Siguiente.

![Figura 55](../images/55.png)

En la siguiente pantalla, hacemos clic en Personalizar permisos.... En la sección Permisos, damos clic en Deshabilitar herencia > Quitar todos los permisos heredados de este objeto. Luego, hacemos clic en Agregar > Seleccionar una entidad de seguridad, buscamos el grupo del departamento, en este caso Contabilidad, le otorgamos todos los permisos excepto Control total y seleccionamos Aceptar.

![Figura 56](../images/56.png)

![Figura 57](../images/57.png)

Ahora, vamos a la sección Compartir, seleccionamos Todos y, seguidamente, hacemos clic en Quitar. Luego, seleccionamos Agregar y repetimos el proceso del punto anterior para agregar Contabilidad y Administradores. A los Administradores les otorgamos Control total y a Contabilidad le damos todos los permisos excepto Control total. Seguidamente, hacemos clic en Aplicar y luego en Aceptar.

![Figura 58](../images/58.png)

Para finalizar, en la pantalla del asistente, damos clic en Siguiente, revisamos que toda la configuración esté correcta y luego hacemos clic en Crear. Repetimos el proceso para cada carpeta del departamento hasta que se vea de la siguiente manera.

![Figura 59](../images/59.png)

En el caso de la carpeta Pública, se crea de la misma forma, con la excepción de que los permisos deben configurarse de la siguiente manera.

![Figura 60](../images/60.png)

Colocando los permisos de esta manera, todos los usuarios tendrán acceso de lectura a la carpeta Pública, pero sólo el personal de TI tendrá acceso de escritura.

Seguidamente, vamos a Herramientas > Administración DFS > Espacios de nombres, hacemos clic derecho y seleccionamos Nuevo espacio de nombres.... Luego, digitamos el nombre del servidor, en nuestro caso Censisoper.

![Figura 61](../images/61.png)

En el nombre del servidor colocamos “Departamentos” y clicamos en siguiente.

![Figura 62](../images/62.png)

En la siguiente pantalla, copiamos el enlace que aparece en “Vista previa del espacio de nombres basado en dominio”, ya que lo necesitaremos más tarde. Luego, seleccionamos Siguiente en las pantallas restantes sin modificar las opciones predeterminadas.

Una vez creado nuestro espacio de nombres damos clic derecho sobre el y seleccionamos Nueva carpeta…, en nombre ponemos el correspondiente al departamento en el caso del ejemplo Contabilidad y en Destinos de carpeta, clicamos en Agregar… > Examinar y buscamos la ruta de la carpeta compartida correspondiente al departamento que creamos anteriormente y le damos a Aceptar.

![Figura 63](../images/63.png)

Repetimos el proceso para cada una de las carpetas del departamento hasta que el espacio de nombres se vea de la siguiente manera.

![Figura 64](../images/64.png)

Por último, nos dirigimos a Herramientas > Administración de directivas de grupo y, dentro de la unidad organizativa CLIENSO, creamos una directiva llamada “Carpetas compartidas”.

Una vez creada nuestra directiva, hacemos clic derecho en Editar > Preferencias > Configuración de Windows > Asignaciones de unidades. Luego, hacemos clic derecho > Nuevo > Unidad asignada. En Acción, seleccionamos Reemplazar, en Ubicación, ponemos el enlace de nuestro espacio de nombres que copiamos anteriormente, marcamos Reconectar y la etiquetamos como “Shares”. En la sección Letra de unidad, marcamos Usar y ponemos la letra S. Dejamos todo lo demás tal como está, luego hacemos clic en Aplicar y finalmente en Aceptar.

![Figura 65](../images/65.png)

Ahora, podemos acceder desde nuestros clientes y ver las carpetas que aparecen según el rol del usuario.

## Cuotas carpetas (tamaños)

Para crear las cuotas de las carpetas compartidas, vamos a Herramientas > Administrador de recursos del servidor de archivos > Administración de cuotas y hacemos clic derecho en "Crear cuota...".

En la ruta de acceso de la cuota, seleccionamos "Examinar" y buscamos la ubicación correspondiente a cada carpeta del departamento. Luego, en la sección “¿Cómo desea configurar las propiedades de la cuota?”, marcamos la opción "Definir propiedades de cuota personalizadas" y damos clic en "Propiedades personalizadas...".

![Figura 66](../images/66.png)

Seguidamente, digitamos el límite según lo indicado en el enunciado para el departamento seleccionado y damos clic en "Aceptar", y luego nuevamente en "Aceptar" en la ventana principal para finalizar la configuración.

![Figura 67](../images/67.png)

Repetimos el proceso para cada una de las carpetas de los departamentos hasta que las cuotas se vean de la siguiente manera.

![Figura 68](../images/68.png)

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

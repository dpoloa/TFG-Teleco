# MiniGUI
Repositorio creado para el TFG de Tecnologías de la Telecomunicación de Daniel Polo Álvarez: MiniGUI (nombre
provisional), estudiante de la Universidad Rey Juan Carlos.
## Objetivo 
El objetivo de este Trabajo de Fin de Grado es crear una GUI (*Graphical User Interface*, por sus siglas en inglés) o 
Interfaz Gráfica de Usuario que permita al usuario poder crear una red de arquitectura de ordenadores a su gusto con
los elementos básicos: hubs, switches, routers y ordenadores/hosts (por ahora, con vistas a añadir controladores SDN en
el futuro). Este programa está escrito en Python, y usa como paquete gráfico Qt, con su adaptación al lenguaje usado 
como PyQt5.
## Historial de versiones
#### Versión 00.01.00
¡Aquí está la primera versión funcional de MiniGUI! Ya es posible crear tu propia red y guardar ciertos campos básicos 
gracias a Mininet, código de libre acceso que permite crear redes de ordenadores a través de hosts y switches haciendo 
uso de las tecnologías OpenFlow y OpenVSwitch (ver http://mininet.org/ para más información, 
https://github.com/mininet/mininet para ver el código base, actualizado cada poco tiempo).

Esta primera versión ofrece al usuario la capacidad de crear sus propios hosts, switches y routers (siendo estos últimos
una versión específica de los switches, por lo que se ha creado una clase específica a partir de una clase base de 
Mininet) y almacenar ciertas características propias como su dirección IP y su ruta por defecto (ruta usada para 
comunicarse con redes con distinto dominio IP), además de poder especificar qué dirección IP tiene el router por cada 
una de sus interfaces.

Además de este anuncio, en esta versión se han introducido diversas mejoras y nuevas funcionalidades:
* Se ha modificado la función changePixmapColor() de la clase NodeGUI, al igual que los controladores de los eventos 
  "hover", para poder ver de forma más visual cada uno de los siguientes casos:
  * Si el elemento tiene la atención de la escena (_"item has focus"_), se añade al icono del elemento una capa de color 
    azulado que se mantiene hasta que la atención de la escena cambie.
  * Si el elemento es sobrevolado por el cursor (eventos _hover_), el elemento tomará un color azulado excepto si el 
  usuario tiene activada la herramienta de borrado (icono papelera), donde dicha capa será de color rojizo.
    
* Arreglado un fallo que no permitía abrir el explorador de archivos en el directorio predeterminado al guardar un 
  proyecto por primera vez o al abrir un proyecto existente.
  
* Se han introducido funciones en las clases NodeGUI, LinkGUI y CanvasGUI para acceder y cambiar atributos, además de 
  poder modificar, añadir o eliminar partes de otras características de la clase.
  
* Se han introducido dos diccionarios que almacenan los punteros a los nodos y los enlaces a través de su nombre para 
  acceder a ellos de una forma fácil y limpia cada vez que sea requerido, además de hacer el código más accesible y 
  claro.
  
* Cada nodo (host, switch y router) tienen su propia ventana de propiedades que puede ser accedida a través del menú 
  contextual cuando la red no está activa. Cuando la red pasa a estar operativa, el menú contextual permite acceder al 
  terminal propio del nodo para poder ejecutar en él los comandos. (*¿Por qué no pruebas a ejecutar un ping?*)
  

#### Versión 00.00.03
En esta versión introducimos algunos de los elementos finales que estarán presentes en la versión 00.01.00: ordenadores, 
switches y routers. Con estos añadidos aparece una nueva función que permite o no la unión entre nodos del sistema (por 
ahora no se permiten, por ejemplo, uniones entre ordenadores). Además, se han realizado los siguientes cambios:
* Se ha modificado la forma que tiene el programa de hacer aparecer un nodo cuando el usuario hacía click en la escena. 
  Además, para poder mantener la funcionalidad de versiones anteriores, otras funciones se han visto modificadas.
  
* Se ha corregido un error que provocaba que las etiquetas de los nodos saliesen descentradas.

* Se ha mejorado la comprobación de enlace entre dos nodos. En la anterior versión no se comprobaba si los dos elementos 
  ya habían sido previamente enlazados, mientras que en la nueva versión sí se corrige.
  
* También se han añadido dos nuevos atributos en la clase NodeGUI (width, height) para armonizar todos los valores de 
  tamaño de los iconos. Además, se han comenzado a añadir propiedades propias de Mininet en dicha clase, como puede ser 
  la dirección IP.
  
* Antes de que el usuario pueda darle una dirección IP específica al nuevo elemento, el programa le asigna una IP 
  predeterminada. Además, la IP queda siempre reflejada en la escena al unirse al elemento como etiqueta.
#### Versión 00.00.02
En esta versión se han realizado los siguientes cambios:
* Se ha añadido un botón para eliminar elementos y hacer más accesible esta funcionalidad para el usuario.
  
* Se ha añadido la funcionalidad de "marcar" un elemento: si el usuario clica sobre algún nodo/enlace de la escena, 
  alrededor del elemento saldrá una línea discontinua. Además, el elemento mantendrá un color más llamativo para marcar 
  que ha sido el último en elegirse. 
  
* Se ha añadido una nueva funcionalidad: el programa avisa al usuario antes de salir del programa, crear o abrir un 
  nuevo proyecto en el caso de que no haya guardado el proyecto actual. Además, para saber en qué proyecto se encuentra 
  el usuario, el título de la ventana se modifica tomando como apellido el nombre del proyecto.
  
* Se han añadido los botones de arrancado y apagado de Mininet. Por ahora, estos botones no realizan ninguna tarea; su 
  funcionalidad será añadida en versiones posteriores.

* Se han modificado tanto el nombre de algunas funciones como su contenido para conseguir una mejor comprensión del 
  código

#### Versión 00.00.01
Se ha subido una primera versión de cómo puede funcionar la parte visual del programa. Por ahora se
puede elegir entre dos "herramientas" (casa, coche) y se pueden unir entre ellas a través de la herramienta "enlace" 
(por ahora se permite enlazar cualquier elemento entre sí). Se pueden mover los elementos libremente, además de que los
enlaces son capaces de seguir el movimiento que realizan los elementos a los que están unidos. Para eliminar cualquier 
elemento, el usuario debe seleccionarlo primero y luego pulsar la tecla Suprimir.

También se ha implementado una primera versión del archivo de guardado, así como una función de lectura de dichos
archivos que permite recuperar los diagramas creados anteriormente. Este archivo de guardado está escrito en lenguaje
JSON.

Por último, se ha añadido un modo oscuro a la aplicación para dar al usuario la posibilidad de poder alternar entre
los dos temas de forma rápida y sencilla.
#UWE Meta modelo y Semblanza#

##Guía del Usuario y Referencia##


Programming and Software Engineering Unit (PST) 
Institute for Informatics 

Ludwig-Maximilians-Universität München, Germany 
Programming and Software Engineering (PST) 

www.pst.ifi.lmu.de/projekte/uwe 

February 2008  

Esta investigación ha sido parcialmente respaldada por el proyecto MAEWA
Model Driven Development of
Web Applications (WI841/7-1) de la Deutsche Forschungsgemeinschaft (DFG), Alemania y la EC 6th Framework proyecto SENSORIA

Software Engineering for Service-Oriented Overlay Computers (IST 016004). 


 
##Índice de Contenidos##
1.  INTRODUCCIÓN 

2.  PAQUETE DE REQUERIMIENTOS

3.  PAQUETE DE CONTENIDOS

4.  PAQUETE DE NAVEGACIÓN

  4.1. DESCRIPCIÓN DE CLASES 

    4.1.1.  Node

      4.1.2.  Link

      4.1.3.  NavigationClass

      4.1.4.  NavigationProperty

      4.1.5.  NavigationLink

      4.1.6.  Menu

      4.1.7.  AccessPrimitive

      4.1.8.  Index

      4.1.9.  Query

      4.1.10.  GuidedTour

5.  PAQUETE DE PRESENTACIÓN

  5.1.  DESCRIPCIÓN DE CLASES

    5.1.1.  PresentationElement

    5.1.2.  PresentationClass   

    5.1.3.  PresentationProperty

    5.1.4.  Page

    5.1.5.  PresentationGroup

    5.1.6.  UIElement

    5.1.7.  UIContainer

    5.1.8.  Form

    5.1.9.  AnchoredCollection

    5.1.10.  Anchor

    5.1.11.  Button

    5.1.12.  Text

    5.1.13.  Image

    5.1.14.  TextInput

    5.1.15.  Choice

6.  PAQUETE DE PROCESOS

  6.1.  DESCRIPCIÓN DE CLASES

    6.1.1.  ProcessClass

    6.1.2.  ProcessLink

    6.1.3.  ProcessProperty

    6.1.4.  UserAction

7.  UWE DESCRIPCIÓN

8.  EJEMPLO: PORTAL SENCILLO DE MÚSICA

  8.1.  CASOS DE USO

  8.2.  MODELO DE CONTENIDO

  8.3.  MODELO DE USUARIO

  8.4.  MODELO DE NAVEGACIÓN

  8.5.  PROCESO DE NEGOCIOS

    8.5.1.  Proceso Login

    8.5.2.  Proceso Logout

    8.5.3.  Proceso BuyAlbum

    8.5.4.  Proceso Register

    8.5.5.  Proceso Recharge

 8.6.  MODELO DE PRESENTACIÓN

9.  REFERENCIAS


##1. Introducción##

Las propuestas de Modelado Web esta orientado por la separación de los aspectos que describen un sistema web,
tales como contenido, estructura de hipertexto, presentación, y procesos. La propuesta Ingeniería web
basada en UML (UWE por sus siglas en Ingles) provee un conjunto de elementos específicos del modelo de dominio web para
el modelado de diferentes aspectos. Estos elementos del modelo y las relaciones entre ellos
están especificados por el meta-modelo.

El meta-modelo UWE como una extensión conservadora del meta-modelo de UML 2.0.
Entendiendo por conservadora que los elementos dl meta-modelo de UML no ha sido modificado.
En lugar de ello, todos los nuevos elementos del meta-modelo UWE están relacionados por herencia con al menos
un elemento del meta-modelo UML. Hemos definido propiedades y relaciones adicionales
para estos nuevos elementos. De forma análoga a loque dictan las buenas prácticas en la especificación de UML,
usamos restriciones OCL para especificar la semantica adicional de estos nuevos elementos.

El meta-modelo de UWE resultante es perfilable, esto significa que es posible mapear el 
meta-modelo como un perfil UML [1]. En especial, UWE es compatible con MOF, p.e. UWE es 
compatible con el meta-modelo de intercambio MOF y por lo tanto con herramientas basadas
en el correspondiente formato de intercambio XML (XMI). La ventaja es que todas las herramientas
CASE UML estandar pueden soportar perfiles UML or usar mecanismos de extensión de UML para
crear modelos de aplicaciones web con UWE. De ser posible estas herramientas case tambien 
pueden ser extendida para soportar los metodos UWE, p.e. la generación automatica de modelos en secuencia.
ArgoUWE y MagicDraw tienen versiones de herramientas CASE que proveen soporte para UWE basandose en
el meta-modelo de UWE.

La extensión UWE del meta-modelo UML consiste en adicionar dos paquetes de alto nivel: Core
y Adaptivity a UML (ver figura 1). La separación de cada aspecto de la aplicación web se encuentra
reflejado por la estructura del paquete Core, la separacion de la adaptacion por la dependencia 
de Adaptivity con Core.


![Vista general del meta-modelo UWE.](/images/ "UWE Meta Modelo")

_Figura 1: Vista general del meta-modelo UWE._


##2. Paquete Requirements (Requerimientos)##

El paquete Requirements contiene las extensiones UWE que son usadas en modelos de casos de uso para discernimiento 
navegacional desde procesos de negocios y casos de uso personalizados, y las extensiones para diagramas de
actividad. Los detalles adicionales acerca de estos elementos seran proporcionados en la siguiente versión de este reporte.

##3. Paquete Content (Contenido)##

El modelado de contenidos para aplicaciones web con UWE no difiere del modelado de contenidos de 
software no web. Por esta razón, usamos elementos del modelo UML para modelar la estructura de
clases, asociaciones y paquetes. Adicionalmente, en el modelado del comportamiento se puede hacer 
uso de características de UML tales como máquinas de estado y diagramas de secuencia.

Las aplicaciones web personalizadas requieren el modelado de características del entorno del usuario. Un perfil
o modelo del usuario puede ser usado para representar estas caracteristicas separando el perfil del usuario del 
modelo de contenido.

##4. Paquete Navigation (Navegacion)##

El meta-modelo de navegación de UWE se muestra en la Figura 2.
La espina dorsal del meta-modelo de navegación es el par de metaclases abstractas Node(Nodo)
y Link (enlace) is las asociaciones entre estas. Un conjunto de subclases de Node y Link 
proveen las meta clases específicas del dominio web para construir el modelo de navegación:
NavigationClass y ProcessClass con los relacionados NavigationLink y ProcessLink asi como
Menu y las promitivas de acceso Index, GuideTour y Query:


![picture alt](/images/photo.jpeg "Title is optional")

_Figura 2: El Paquete de Navegación_

Las relación entre los elementos del modelo del paquete de Navegación y las clases UML usadas para 
modelar el contenido de una aplicación web se muestra en la Figura 3.

![picture alt](/images/photo.jpeg "Title is optional")

_Figura 3: Relaciones del paquete de Navegación con UML_

##4.1. Descripción de clases##

###4.1.1. Node (Nodo)###

Hablando de manera abstracta, un nodo puede ser cualquier tipo de nodo en un gráfico de navegación. Es significa
generalmente que cuando se alcanza un nodo mientras se navega, se provee al usuario con alguna
información y opcionalmente se le ofrece la posibilidad de realizar una o mas acciones.
Un nodo no representa necesariamente una pagina de la aplicación web, sin embargo es posible que sea así.

**Generalizaciones**
 *  Class (de UML)

****Atributos****
 *  isLandmark : Booleano especifica cuando en nodo es un marcador, lo cual
 significa que se puede alcanzar desde cualquier otro nodo de diagrama de navegación.

****Asociaciones****
 *  nLinks : Link [&42;]  La colección de enlaces que apuntan al nodo.
 *  outLinks : Link [&42;] La colección de enlaces que se originan en el nodo.

###4.1.2. Link###

Un link (enlace) es una linea del diagrama de navegación y por tanto conecta dos nodos. Recordemos
que un nodo no siempre representa una página, un enlace no tiene que representar una página
de transición que se desencadena por una acción del usuario. Como menciono en la sección 5, el modelo de presentación 
define en cualquier caso la información de dos nodos que se encuentran conectados por un enlace que es mostrado al 
simultáneamente o si el usuario ha pulsado en un ancla para navegar de un nodo a otro (ver la sección 5 para más información)

**Generalización** 
 *  Association (de UML)

**Atributos**
 *  isAutomatic : Booleano Este atributo permite especificar de forma explícita que no se
 requiere decisión del usuario para seguir el enlace.

**Asociaciones**
 *  source : Node [1] El nodo de origen del enlace.
 *  target : Node [1..&#42;] El nodo destino del enlace. Se utilizan multiples nodos
 destino por adaptabilidad, esto no esta descrito en esta versión del documento.


4.1.3. NavigationClass

Una clase de navegación representa un nodo navegable de la estructura de hipertexto y establece la
conexión entre el modelo de navegación y el modelo de contenido. Una clase de navegación que esta 
asociada con una clase del modelo de contenido es traducida para representar el contenido de una 
instancia de esa clase.

**Generalización**

 *  Node

**Atributos**
 Sin atributos adicionales

**Asociaciones**
 *  contentclass : Class [0..1] La clase del modelo de contenido que especifica el 
 contenido de la clase de navegación.
 *  menus : Menu [&42;] La colección de todos los menús que son alcanzables
 directamente desde la clase de navegación. p.e. menús que 
 compuestos por enlaces de navegación que se originan de la clase de navegación.
 *  navigationProperty : NavigationProperty [&42;] { subsets ownedAttribute } 
 La colección de propiedades de navegación que define  el contenido de la clase de navegación.

4.1.4. NavigationProperty

Los atributos de una clase de navegación son llamados propiedades de navegación. Estos definen el contenido 
de los elementos de la UI (User Interface). El valor de una propiedad de navegación es tomado también de una propiedad
asociada de una clase de contenido o derivado usando una expresión de selección. Hasta ahora, UWE no
especifica ninguna sintaxis o semántica especial o lenguaje alguno que pueda usarse para la expresión de selección.

Es una práctica común en diagramas de navegación el omitir propiedades de navegación que estén
conectadas a propiedades de la clase de contenido (content class). A pesar de esto, estas también pueden especificarse de 
indicando que información es relevante. Si la clase de navegación no tiene ninguna propiedad de navegación,
entonces cada propiedad de la clase de contenido es de forma implícita representada por una propiedad de navegación 
"virtual" con el mismo nombre.

**Generalización**

 *  Property (de UML)

**Atributos**

 *  selectionExpresion : String [0..1] Una expresión que tiene el mismo tipo
 que la propiedad de navegación y que es usada para derivar un valor
 del conjunto de instancias de clase de contenido disponibles actualmente.
 El contexto de la expresión (el mismo en OCL) es la clase de contenido que
 esta asociada con la clase de navegación.

**Atributos**
Sin atributos adicionales.

Asociación
Sin asociaciones adicionales.

4.1.6. Menu

Un menú se usa para manejar rutas de navegación alternativas. Nótese que un menú en el modelo
de navegación no se muestra siempre como un menú en el sentido de la interfaces de usuario. Esto se debe 
a que dos nodos que están conectados a través de un menú podrían haberse establecido que se muestren simultaneamente
en el modelo de presentación (ver sección 5). En este caso, el usuario no tiene que hacer nada para
seguir la ruta de navegación, lo cual debe ser el comportamiento esencial de un menú en cualquier 
interfaz de usuario.

**GEneralizaciones**

 *  Link

**Atributos**

 Sin atributos adicionales

**Asociaciones**

 *  navigationClass : NavigationClass [0..1] La clase de navegación que es el origen de 
 todas las rutas de navegación a través del menú.


 4.1.7. AccessPrimitive (Primitivas de acceso)

 Las primitivas de acceso son usadas para seleccionar las instancias de las clases de contenido que 
constituyen el contenido de las clases de navegación.

**GEneralizaciones**
 *  Node

**Atributos**
 Sin atributos adicionales

**Asociaciones**
 *  accessedAttributes: NavigationProperty [&42;]  Una colección de propiedades 
 de navegación que son usadas para seleccionar la instancia de la clase de contenido.

4.1.8.  Index

Un index(índice) permite seleccionar una instancia de la clase de contenido de un conjunto de instancias que 
han sido colectadas mientras se navega. Esto significa que un conjunto de instancias de la clase de contenido se toma
del contexto del predecesor en la ruta de navegación y el usuario puede escoger uno de ellos.
La instancia seleccionada se convierte entonces en el objeto de contenido para la clase de navegación 
cuando se sigue el indice en la ruta de navegación.

El conjunto de clases de contenido de entrada esta determinado por el enlace de navegación entrante.
Existen tres clases diferentes:

 1.  El predecesor es una consulta (query). En este caso, el conjunto de instancias es simplemente el resultado
 de la consulta, p.e. todos los libros publicados en Diciembre de 2007.
 2.  El predecesor es una clase de navegación. El conjunto de instancias es tomado de una
 colección de propiedades de la correspondiente clase de contenido. Para especificar cual propiedad es 
 usada, el nombre del rol del enlace de navegación puede ser igual al nombre de la propiedad.
 3.  El predecesor es un menú. En este caso, el contexto del menú predecesor de la
 clase de navegación es usado como si estuviese conectado directamente y se aplican las reglas 
 descritas en 2. En el ejemplo del Portal de Música al final del documento, esta configuración 
 es un role navegable nombrado ownedAlbums. Esto significa que el conjunto de entrada de álbumes 
 para UserAlbumIndex se toma del rol ownedAlbums de la clase Usuario desde el modelo usuario (ver sección 8.3).

**Generalización**

 *  AccessPrimitive

**Atributos**

Sin atributos adicionales

**Asociaciones**

Sin atributos adicionales


4.1.9  Query

Una consulta (query) es usada para obtener contenido desde una fuente de datos. A diferencia de un índice, una consulta no
da un conjunto de instancias de clase de contenido de un predecesor de la ruta de navegación, pero si desde una
base de datos o cualquier otro tipo de fuente de datos que soporte consultas. Una consulta puede requerir parámetros 
de búsqueda, como p.e. para buscar películas por título. En este caso, el modelo de presentación debe contener
elementos que provean una interfaz de usuario para llevar los valores de los parámetros (ver sección 5).
La semántica de una consulta puede ser especificada usando la propiedad filterExpression de la Consulta,
la cual puede recibir una expresión que describe la consulta y que incluye los accessedAttributes (ver Figura 10).

Si la consulta no requiere parámetros, esta se ejecuta automáticamente cuando es alcanzada en el 
gráfico de navegación. Un ejemplo puede ser una consulta que retorne las 10 películas mas populares actualmente
desde la base de dato de películas.

**Generalización**

 *  AccessPrimitive

**Atributos**

 *  filterExpression : String [0..1] Una expresión que describe la semántica de la consulta.

**Asociaciones**

 Sin asociaciones adicionales

4.1.10  GuideTour (Paseo Guiado)

Un paseo guiado provee procesos secuenciales para instancias de clase de navegación. Esto es dado
un conjunto ordenado de instancias de clase de contenido como entrada y teniendo una enlace de navegación saliente a una
clase de navegación. El usuario puede ir hacia atrás y hacia adelante a través de la colección de entrada
seleccionando una instancia a la vez como contenido para la clase de navegación cargada. El orden en el
cual la instancias son visitadas se especifica usando una expresión de filtrado.

**Generalización**

 *  AccessPrimitive

**Atributos**

 *  filterExpression : String [0..1] Una expresión que es usada para calcular el orden in el cual
 las instancias de la clase de navegación son visitadas.

**Asociaciones**

Sin asociaciones adicionales.


5.  Paquete de Presentación 

El modelo de presentación provee una vista abstracta de la interfaz de usuario (UI) de una aplicación
web. Este se basa en el modelo de navegación. El modelo de presentación se abstrae de aspectos
concretos de la UI, como el uso de colores, fuentes, y la disposición de  los elementos de la UI 
en la página web; en lugar de ello, el modelo de presentación describe la estructura básica de la interfaz
de usuario, p.e., que elementos de la UI (e.g. texto, imágenes, anclas, formularios) son usados para presentar los
nodos de navegación (ver Figura 4y Figura 5). Notese, los elementos de la UI no representan componentes concretos
de ninguna tecnología de presentación si no que describe que funcionalidad se requiere en ese punto
particular en la interfaz de usuario. Esto puede significar simplemente que debe mostrarse una imagen o texto
o por ejemplo que el usuario debe desencadenar una transición en el modelo de navegación. En el último caso,
es claro que se puede usar un Anchor (ancla) en el modelo de presentación UWE, pero UWE no define como se debe
representar el ancla en la aplicación web final. Esta podría ser de hecho simplemente un elemento anchor de HTML (<a>),
pero tambien un botón o bien hasta un applet flash incrustado puede servir a este proposito.

Los elementos básicos del un modelo de presentación son las clases de presentación, las que están
basada directamente en nodos del modelo de navegación, p.e. clases de navegación, menús, primitivas de acceso,
y clases de proceso. Las clases de presentación pueden contener otros elementos de presentación. Es se 
hace por medio de propiedades de presentación las que usan los elementos de presentación como tipo.
En el caso de los elementos UI, como imágenes o texto, la propiedad de presentación es asociada
con una propiedad de navegación que porta el contenido a ser mostrado.

En contraste a las clases y páginas de presentación, un grupo de presentación define un conjunto de
clases de presentación que se muestran alternativamente, dependiendo de la navegación. En el sentido de la
descripción anterior, un grupo de presentación crea un conjunto de arboles de alternativas de inclusión.


![picture alt](/images/photo.jpeg "Title is optional")
Figura 4: La columna vertebral del Paquete de Presentación

![picture alt](/images/photo.jpeg "Title is optional")
Figura 5: Elementos de Presentación

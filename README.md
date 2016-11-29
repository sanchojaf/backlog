# backlog

Orden recomendado: 

- Pacheco: 69, 24, 59, 61, 36, 1, 3

- Mary: 29, 50, 37, 56, 57, 46, 28, 45, 27, 30

- Aneli:  62,  20, 54, 63, 64, 66

- Mac: 53, 34, 58, 21, 60, 52, 33, 51, 5, 12, 9, 15, 14, 44, 26, 16, 39, 41, 43, 47


### 71. Agregar graficos de visualizacion de los modelos. [Aneli]

Agregar graficos de visualizacion de los modelos usando 

https://github.com/cenit-io/rails_admin_dynamic_charts

Es posible que sea necesario hacer cambios en la gema.

Por otra parte los graficios deben poder renderearse invocando una tarea de background, de modo que no se quede la pagina cargango.

Deberian mostrar toda las filas y no solo las correspondientes a la pagina actual.

### 70. Implementar una ventana flotante de contact us. [Aneli]

esta rama tiene la logica adelantada pero no esta funcionando.

	https://github.com/cenit-io/cenit/tree/add_contact_us

### 69. Mejoras a la acccion REST API. [Pacheco]

Como complemento a lo que ya esta podriamos tener una primera version

de codigo para Python, Ruby y JS aun sin tener los clientes SDK correspondientes.

Podemos usar bibliotecas HTTP de cada lenguaje.

Ejemplo de cURL en Parse (retrieving a user):

```bath
curl -X GET \
  -H "X-Parse-Application-Id: ${APPLICATION_ID}" \
  -H "X-Parse-REST-API-Key: ${REST_API_KEY}" \
  https://api.parse.com/1/users/g7y9tkhB7O
```

Ejemplo en Python usando biblioteca HTTP (retrieving a user):

```Python
import json,httplib
connection = httplib.HTTPSConnection('api.parse.com', 443)
connection.connect()
connection.request('GET', '/1/users/g7y9tkhB7O', '', {
       "X-Parse-Application-Id": "${APPLICATION_ID}",
       "X-Parse-REST-API-Key": "${REST_API_KEY}"
     })
result = json.loads(connection.getresponse().read())
print result
```

ver el ejemplo aqui

	http://parseplatform.github.io/docs/rest/guide/#retrieving-users


De modo que la seccion donde ahora se muestra el cURL, podriamos tener 4 tabs: cURL (predeterminado), Ruby, Python, JS. 

Cada uno con el codigo correspondiente.

Agregar como una ultima seccion un boton run, que permita ejecutar el request y mostrar el response debajo, con un scroll.


### 66. Adicionar un Save Filter [Aneli]

El modelo Query fue renombrado como Filter, por varias razones:

1- Para usar el mismo nombre que usa rails_admin, al final es persistir los filtros actuales que ellos tienen en las vistas

2- Para reservar el termino Query, al nuevo API [GraphQL](http://graphql.org/)

Con este nuevo nombre es mas intuitivo poder hacer la funcionalidad de salvar un filtro dinamico cuando se adicione a una vista cualquiera. O sea esta seria una forma alternativa a la forma actual (que es el al modelo Filter y crear un nuevo filter). En las vistas de rails_admin por default viene un Add Filter, una vez selecionado Add Filter apareceria un boton asociado 'Save' para poder persistir el filtro.


### 64. Usar el mismo estilo de codigo en Show que en los Edit. [Aneli]

La propuesta es poder utilizar el mismo estilo de codemirror para el codigo en las vistas Show que en las vistas Edit, con la diferencia de que el codigo en los Show no puede ser Editable.

### 63. Lanzar el Tour automáticamente. [Aneli]

Que el tour se lance automaticamente, la primera vez que alguien se loguea, o se conecta desde un IP.
### 62. Completar las categorias y tags de las Shared Collections. [Aneli, Mac]

En el menu lateral:

* que aparezca primero My Collections y Luego Shared Collections.

* Agregar un subnivel a las Shared Collections, con las categorias de las Shared Collection


Tomaremos de base este listado de categorias que aparece en APIs-guru, que fue un trabajo que hicimos junto con ellos.

	https://github.com/APIs-guru/openapi-directory/blob/master/resources/categories.yaml

  * Analytics
  * Backend
  * Cloud
  * Collaboration
  * Customer Relation
  * Developer Tools
  * eCommerce
  * Education
  * Email
  * Enterprise
  * Financial
  * Frontend
  * Forms
  * Hosting
  * IoT
  * Location
  * Machine Learning
  * Marketing
  * Media
  * Messaging
  * Monitoring
  * Open Data
  * Payment
  * Project Management
  * Search
  * Social
  * Support
  * Telecom
  * Text
  * Time Management
  * Tools

En Guru API, esta definido el nombre y la definicion de la categoria.

Cada fichero path.yaml en api guru, tiene la categoria correspondiente al API. Ejemplo:

   https://github.com/APIs-guru/openapi-directory/blob/master/APIs/backupify.com/patch.yaml#L8-L9

Tener en public un fichero, categories.yaml local, donde podamos completar las categorias que no estan en guru api.

Valorar (Con Mac) la posibilidad de que se pueda asociar mas de una categoria.

La diferencia entre Categoria y Tag que vamos a seguir es que la categoria es un diccionario que debe cambiar muy poco, y cada categoria debe reflejar al menos catidad minimas de Shared Collections. En corresondencia con la definicion de Guru API.


    # List of categories to be used in `x-apisguru-categories`.
    #
    # Intention is to have list of categories that can fitted as sidebar on a single page.
    # With this constrain in mind we can't have ideal fit for each API, instead we
    # choose approach of open-ended categories.
    #
    # Rules:
    #  - categories names consist of following symbols 'a-z_'.
    #  - for each category user-friendly title and description provided.
    #  - removal of category is breaking change.
    #
    # Warning: Future addition of categories is possible, but it should be proven that
    # significant amount of APIs don't fit any of existing categories.
  

Los Tags ademas es un concepto que asociaremos a otros modelos en Cenit.

Los tag pueden ser terminos propios de cada shared collection.

Completar los tags de las shared collection, en princio con los que aparecen en guru api en el path.yml. Ejemplo:

    
    https://github.com/APIs-guru/openapi-directory/blob/master/APIs/backupify.com/patch.yaml#L11-L16

Tener en un fichero publico para los tags, tags.yaml, donde podamos completar las tags que no estan en guru api para las shared collections.

### 61. Salvar los ficheros en AWS S3. [Pacheco]
 
Actualmente los ficheros que son Files Data Types, son almacenados en MongoDB.
 
Aunque es una variante rapida y sencilla para almacenar los ficheros, no es la forma mas escalable para guardar grandes volumenes de ficheros.
 
Si eliminar la opcion de almacenar en la base de datos, seria conveniente poder adicionar AWS S3 como una opcion de almacenamiento, que ademas se la opcion que configuremos para produccion en el server.

### 60. Control de Acceso basado en Roles (ACLs) para Users y Connections. [Mac]

1. Cada Usuario tiene asociado un Role.

2. Cada Coneccion debe tener un Role, por default tomara el role del Usario que la crea.

3. Un Role se definira con dos conjuntos de permisos: Permisos de Lectura, Permisos de Escritura.

4. Cada Permiso estara asociado a un Data Type, de cualquier tipo: Inner Type, Object Type o File Type.

5. Como opcion avanzada el Permiso listara las acciones del Data Type, las cuales pueden ser activadas o desactivas.  

6. Un usuario podra crear nuevos roles (excepto, que no tenga acceso al modelo Role).

7. Los roles (excepto Super-Admin) debe tener un Role Padre, por default sera el Role del usuario.

8. Un Role solo podran restrigir los permisos del Role Padre.

9. Se podra Invitar, definiendo el Role del nuevo usuario, por default tomara el Role del usuario que invita.

### 59. Cenit CodeGen para la generación de SDKs [Pacheco]

En lugar de tener proyectos independiente con los diferentes SDK, podemos tener un proyecto Cenit-CodeGen, para la generación automática de las SDKs de Cenit.

Con bastante similitudes al proyecto CodeGen de Swagger

	https://github.com/swagger-api/swagger-codegen

Que basado en un Swagger Spec genera el codigo correspondiente de un grupo de SDK.

En nuestro caso sacariamos ventaja de ser un caso particular para Cenit, generando a partir del Swagger de Cenit, y de cuaquier otro elemento que necesitamos para los cambios que sean necesarios para nuestros SDKs.

Esta generación podemos hacerlo en dos variantes:
 
* Desde cero, usando node.js como en cenit2oddoo o quizas usando ruby.
* O con un fork o clone del repo swagger-codegen (que está basado en Java)

Es importante notar que la especificación Swagger del API de Cenit será generada automáticamente por Cenit, en lo que está trabajando Mac. De modo que no será necesario en el futuro actualizar el swagger.yml de forma manual como estamos haciendo hasta ahora.

Los 3 primeros SDK deben ser:

* Ruby 
* Python
* JS (node.js)

Cada SDK del proyecto Cenit CodeGen, seria generado hacia un repo independiente. La generación de repos es una de las funcionalidades que tiene el proyecto swagger-codegen

Como referencia adicional, seria muy bueno poder revisar los SDK de Parser.io y poderlos comparar con nuestra generacion.

* Parse JS https://github.com/ParsePlatform/Parse-SDK-JS 
* Parse Python https://github.com/milesrichardson/ParsePy

En el caso de Parse, es muy importante los SDK para móviles y dispositivos de IoT, que luego debemos adicionar como un 2do grupo de SDK para poder cubrir la posibilidad de que se pueda hacer push a Cenit desde dispositivos móviles

* Parse iOS https://github.com/ParsePlatform/Parse-SDK-iOS-OSX
* Parse Androi https://github.com/ParsePlatform/Parse-SDK-Android
* Parse Arduino https://github.com/ParsePlatform/Parse-SDK-Arduino
* Parse Embedded C  https://github.com/parseplatform/parse-embedded-sdks 

### 58. Cambios a partir del nuevo concepto de Query. [Mac]

Se introdujo el nuevo concepto de Query en tab Compute. Que permite:

* Asociar a un Data Type un filtro o query. 
* El filtro se define con la mismo UI que se usa en Observer, que es a su vez similar a la de rails_admin asociada a los filtros de las vistas index.
* En el show aparece un nuevo 'Segment', que abre la vista de index correspondinte con el filtro aplicado. 

A partir de estos cambios es conveniete refactorizar Observer, de modo que en lugar de tener un campo data type y triggers, tenga asociado una Query.

### 57. Crear Shared Collection de Oscar. [Mary]

```bash
$ git clone https://github.com/django-oscar/django-oscar.git
$ cd django-oscar
$ mkvirtualenv oscar  # needs virtualenvwrapper
(oscar) $ make sandbox
(oscar) $ sites/sandbox/manage.py runserver
```

Si no tienes instalado mkvirtualenv

```bash
$ virtualenv oscar
$ source ./oscar/bin/activate
(oscar) $
```

luego para entrar a la administracion

    http://localhost:8000/
    
y click en login, el super usuario tiene las siguientes credenciales

```
username: superuser
email: superuser@example.com
password: testing
```

O puedes lanzar una aplicacion de sandbox con el API

```
$ mkvirtualenv oscarapi
$ git clone https://github.com/django-oscar/django-oscar-api.git
$ cd django-oscar-api
$ make sandbox

# run the server
$ python sandbox/manage.py runserver
```

    http://localhost:8000/api

[Sandbox documentacion](http://django-oscar.readthedocs.io/en/releases-1.1/internals/sandbox.html) 

El API es una aplicacion independiente que hay que instalar

https://github.com/django-oscar/django-oscar-api



### 56. Crear Shared Collection de Spree. [Mary]

Pasos para crear lanzar una tienda de Spree con productos de ejemplo

```bash
$ git clone git@github.com:spree/spree.git
$ cd spree
$ bundle
$ bundle exec rake sandbox
$ cd sandbox 
$ rails s
```

luego para entrar a la administracion

    localhost:3000/admin

```
  user: spree@example.com
  pass: spree123
```

Ahi se puede ir a Users por el menu lateral izquierdo

y entrar al edit de spree@example.com

ahi se muestran las credencials del api, ejemplo

```
API Access: 
KEY:  cf86f7785b4b7a4d22ae86af18b3e9bc8ee7baa283e1a893
```

La documentacion del API, puedes encontrarla aqui

[Doccumentacion del API](http://guides.spreecommerce.org/api/)

un manera sencilla de ver todas las rutas del api es

    rake routes

Puedes imprimirlas para un fichero, 

    rake routes > tmp/routes.txt

y luego ahi revisar las rutas del api.

aqui estan las rutas en un gist

[link rutas del api de spree](https://gist.github.com/sanchojaf/29e7845987bfe22b81c6437b9692a00a)

### 54. Migrar a rails_admin 1.0. [Aneli]

Rails Admin hizo el release de la version 1.0, por lo que es un buen momento para hacer un upgrade de Cenit. Es importante revisar todas las vistas que tenemos customizadas en Cenit.

### 53. Modelos para soportar API SPec sincronizacion con Sagger. [Mac]

Para formalizar un API Connection vamos a seguir en lo posible las convenciones de [Studio Restlet](https://studio.restlet.com)


El API Connection (actualmente Connection en la navegación) puede quedar definido mediante la asociación de los nuevos conceptos:

* Section
* Resources
* Operaciones
* Representation

Seccion es un espacio de nombre que permite agrupar un grupo de Resources (Ejemplo: todos los resource relacionados con User) puede tener asociado varios Representation

[Link new Section](https://studio.restlet.com/apis/28d83b4d-85d0-4b6e-b070-40896102f6b8/new-sections)


Un Resource corresponde a un path en específico (Ejemplo: /user/{userlogin} ) y se asocia a un grupo de Representation y de Operations

[Link new resource](https://studio.restlet.com/apis/28d83b4d-85d0-4b6e-b070-40896102f6b8/new-resource)

Una operation corresponde HTTP Method con los parámetros correspondiente, y la relación son un Resource.

[Link new operation POST](https://studio.restlet.com/apis/28d83b4d-85d0-4b6e-b070-40896102f6b8/resources/~2Fpet~2FfindByStatus/operations/POST)

Un representation es un Wrapper de un JSON Data Type (en la navegacion Definition/Data Type/Object Type) 

[Link new Representation](https://studio.restlet.com/apis/28d83b4d-85d0-4b6e-b070-40896102f6b8/new-representation)

Nota: Los webhooks no lo vamos a modificar, mas adelante se movera a Worflows, para mas detale ver tarea [52]( https://github.com/sanchojaf/backlog#52-concepto-de-notificación-paradigma-pushnotification-mac)

Una version inicial de los modelos es en esta rama

[add_new_model_resource](https://github.com/cenit-io/cenit/tree/add_new_model_resource)

los cambios se pueden ver bien en el 

[pull reuquest](https://github.com/cenit-io/cenit/pull/964/files)

La idea es sincronizar el swagger de la tarea [24] con estos modelos. 

### 52. Concepto de Notificación (paradigma Push/Notification). [Mac]

Nota: A lo que llamamos actualmente como Notifications, le debemos llamar System Notifications, de modo que este Notification es otro concepto

Con algunos cambios menores podemos acercarnos a modelar el concepto de Notificación en el paradigma Push/Notification, usado sobre todo para aplicaciones móviles, con uso también en sistemas de marketing email, y otros sistema de notificación e integración.

Por ejemplo en Marketing Email, se hacen flows para enviar correos a un Segmento específico de clientes.

En la  siguiente imagen se pueden ver dos  ejemplos de flujos en [Klavyio](https://www.klaviyo.com) un sistema de Email Marketing, en el primer ejemplo se hace un flujo que envia un correo a un cliente que  abandonó el un checkout, o sea un flujo asociado con un evento  de cambio de estado de la orden.

[link imagen](https://drive.google.com/file/d/0B-ltzH-m3LxTbndPQzBoemNjVU0/view?usp=sharing)

Estos sistema de notificación suelen incluir el envío por SMS y además de  webhooks como una opción de notificación. 

Las notificaciones quedarían de forma natural dentro de la sección de  Worflows


* Workflows
  * Triggers
    * Data Events 
    * Schedulers
  * Flows
  * Notifications
    * Mobile Apps
    * Email
    * SMS
    * Webhook

Con esto podemos resolver otro problema importante, la separación del concepto de Webhooks de los conceptos de API Connection. Haciendo un uso mas apropiado del concepto Webhook. Mientras que la definición de un API Connection quedaría completamente autocontenida, el mapeo entre API Spec y API Connection seria mas directo.


El API Connection puede quedar completamente definido en términos de Resources y Operaciones (este sería un nuevo concepto). Un operation sería un HTTP Method con los parámetros correspondiente, y la relación son un Resource. 


De manera que el webhook quedaría definido por el Connection (que aporta la URL básica), el Operation (que generalmente sera el HTTP POST ) el data type, la relación con el evento y los flows asociados. De modo que desde el Flow podemos ver el webhook asociado, y desde el webhooks podemos ver los flows donde este aparece, idem con los eventos. Esto facilitaria la navegación entre los elementos de worflows.


Los tipos de notificaciones Email y SMS, deben tener un área de configuración donde se defina los servicios de Email y SMS que se van a usar, por ejemplo GMAIL y Twilio.

* Configurations
  * ...
  * Email Config
  * SMS Config

Con los nuevos cambios que permiten definir eventos asociado a los Data Type de modelos del Setup, es posible hacer un flujo donde se envían System Notification por Email (o sea una notificacion de tipo Email)


En una primera etapa podemos tener 3 tipos de notificación definidos: Webhooks, Email, SMS. Quedando pendiente las notificaciones a Mobile Apps. 

Para que el envio de  notificaciones a Mobile Apps, tenga todo el sentido es necesario definir un SDK para Androi y iOS, una opcion es usar (o modificar) los SDK open source de (Parse.io SDKs)[https://parseplatform.github.io/#sdks]
	
Otro elemento que nos ayudaría a aproximarnos mejor al patrón de Push/Notification, es incluir al API de Cenit, una opción push genérica, aunque sea redundante con las opciones de POST que existe en el API, este endpoint Push, puede tener la ventaja de subir en un mismo payload un Json que incluya diferentes tipos de objetos. 

Definiciones de Webhook (Referencias )

A WebHook is an HTTP callback: an HTTP POST that occurs when something happens; a simple event-notification via HTTP POST. A web application implementing WebHooks will POST a message to a URL when certain things happen.

Webhooks are "user-defined HTTP callbacks".[2] They are usually triggered by some event, such as pushing code to a repository[3] or a comment being posted to a blog.[4] When that event occurs, the source site makes an HTTP request to the URI configured for the webhook. Users can configure them to cause events on one site to invoke behaviour on another. The action taken may be anything. Common uses are to trigger builds with continuous integration systems[5] or to notify bug tracking systems.[6] Since they use HTTP, they can be integrated into web services without adding new infrastructure.[7] However, there are also ways to build a message queuing service on top of HTTP—some RESTful examples include IronMQ and RestMS.


### 51. Generar automaticamente el swagger del API de Cenit. [Mac]

A partir de la nueva implementacion de DataTypes asociados con modelos del setup, donde ademas pueden ser asociados data events con esos modelos. Hacer una generacion automatica del swagger.yml que corresponde al API de Cenit, de modo que podamos mantener sincronizado el API con el codigo  de Cenit.

### 47. Habilitar que las notificaciones se envíen por email o SMS. [Mac]

- Poder seleccionar el nivel de notificaciones que serán enviada por email y/o SMS.
- Por default deben ser solo errores o warning
- Tener  la opción de enviar por SMS independiente del envio por email.
- El envío por SMS estaría deshabilitado por default
- Posibilidad de especificar mas de un email, o mas de sms 

### 46. Integracion de Shipstation con la Colleccion generica Ecommerce. [Mary]

Shipstation es la integracion que mas nos han solicitado. Aqui tenemos el caso real de Satechi con los diferentes marketplaces.

Ademas tenemso la integracion con Odoo que tambien fue una solicitud real de un cliente, en lo que trabajo Daniel.

ver tareas: 45, 27 y 2

### 45. Integracion de Odoo con la Colleccion generica Ecommerce. [Mary]

Si tenemos una integracion generica entre Odoo y la Colleccion Ecommerce. Esto puede ayudar a simplificar mucho la integracion con Ecommerce reales como es el caso actual de Magento.

Todo las integraciones con Odoo que sean ecommerce podrian ser una customizacion de esta integacion generica entre Odoo y la Colleccion Ecommerce.

Por demas estas integraciones son de las importantes que aparecen cuando se visita Odoo Apps

- https://www.odoo.com/apps/modules

Ahi se puede ver Magento y Woocommerce, como los addons que mas vendidos.

Para probar este flujo se puede usar, Magento y Spree, para tener dos casos iniciales.

ver tareas: 46, 27 y 2

### 44. Eliminar concepto de Connection Role. [Mac]

Eliminar concepto de *Connection Role* haciendo los cambios pertientes en los modelos que lo referencian, como es el casso de los *FLows*.

Luego de esta tarea se debe actualizar las integraciones en Odoo.

### 43. Definir el Cenit Collection Format como un JSON Schema. [Mac]

En todas las colecciones poner un link que permita visualizar el JSON ‘oficial’ de la colección, que se debe corresponder con el Cenit Collection Format.

### 41. Adicionar los logs de Activity, basado en el history. [Mac]

RailsAdmin tiene extensión para visualizar el historial de actividades para aquellos modelos que sean decorados, este historial aparece en una vista asociada al modelo y en el dashboard. Esa extensión la estamos usando para gestionar las versiones de cross sharing.

Es importante excluir algunos modelos de esta opción como los logs porque tienen una frecuencia muy alta de ocurrencia con relación a otros modelos, es el caso por ejemplo de las tareas y las notificaciones

### 39. Lanzar un flujo al termina la ejecución (de la tarea) de un flujo previo. [Mac]

Permitir que un modo de ejecutar un flujo sea lanzarlo luego de terminada la ejecución de un flujo previo.
Este cambio debe ser suficiente para poder enlazar los flujos y definir ‘dataflows’.

Es importante notar que actualmente los Flow se puede combinar mediante eventos, pero esta alternativa podria ser una manera mas sencilla de relacionar data flows.

De modo que un flujo se podría lanzar de 3 maneras:
Mediante los triggers (data event o schedulers)
De forma manual
Definiendo un flujo previo (el flujo actual se lanzaría al terminar la ejecución del flujo previo)

Estos modos de ejecución no tienen que ser exclusivos

En estos momento hay algo equivalente, mediante la definición de un callback al terminar un flujo, la diferencia básica, es que, en el flujo nuevo es donde se define el flujo previo, esto permite que cuando se termine de ejecutar un flujo ‘B’, se pueda ejecutar múltiples flujos, en caso de abajo ‘B’ y ‘C’.

- \---A 
  - \---B
  - \---C
    - \---D

A- se define como flujo previo en ‘B’ y ‘C’ 

C- se define como flujo previo en ‘D’ 

Es importante notar que ‘B’  podría ser un flujo que lo único que defina sea un traslator de tipo algoritmo, donde la salida del flujo sean datos.

### 37.Usar el background color en el logo de los shared collections. [Mary]

Algunos logos usan color blanco y tienen asociado un color de background, al parercer en los shared collections no estamos usando el background por lo que los logos no se ven bien o nada, ejemplo: infermedica, Jirafe Event API, NeoWs, watchful.

### 36. Menu lateral de Objetos. [Pacheco, Aneli]

Propuesta: Cuando se de click a un elemento hoja de este menu lateral actual, debe cambiar a un menu de objectos relacionado con el elemento seleccionado.

Por ejemplo si vamos a API Connectors, y le damos click a un connection en particular el menu contextual de objetos podria lucir como el siguiente jerarquia:

- PetStore (Collection Name)
  - PetStore API - v1 (API Connection Name)
    - /pet/findByTags (Resouce Name)
      - Get FindByID (Webhook Name)
  ...    
- Uber (Collection Name)
  - Uber Rest API - v1 (API Connection Name)
  ...
  
Tendriamos un boton flotante con un over que permita cambiar del menu contextual de objetos al menu standard.  

Revisar la parte final de esta presentacion.

- https://docs.google.com/presentation/d/1U7npFSNCPMDZDrDZyPNuP9blxEZmcxFGkDDvTFm2nqw/edit?usp=sharing

### 34. :bug: Errores en los algoritmos en produccion. [Mac]

1. En las entrada de los algorimo *Array* no aparece como un tipo valido

2. Implementando los algoritmos que aparecen aqui

https://www.sitepoint.com/algorithmic-fun-ruby-hashes/

Version 1:
```ruby
if (n % 3 == 0) && (n % 5 != 0)
  'Fizz'
elsif (n % 3 != 0) && (n % 5 == 0)
  'Buzz'
elsif (n % 3 == 0) && (n % 5 == 0)
  'FizzBuzz'
else n
end
```

Version 2:
```ruby
 h = {
    'Fizz' => (n % 3 == 0) && (n % 5 != 0),
    'Buzz' => (n % 3 != 0) && (n % 5 == 0),
    'FizzBuzz' => (n % 3 == 0) && (n % 5 == 0),
    n => (n % 3 != 0) && (n % 5 != 0)
  }
  h.key(true)
```

Salida esperada en los casos:
```ruby
puts declarative(2) #=> 2
puts declarative(3) #=> Fizz
puts declarative(5) #=> Buzz
puts declarative(7) #=> 7
puts declarative(15)#=> FizzBuzz
```
Las dos versiones dan error

### 33. Añadir el concepto de Resource en la categoria de Connectors. [Mac]

Para poder lograr una mayor correspondencia entre los conceptos de Connectors y una especificacion formal de API (como Sagger) es importante introducir el concepto de Resource

Se debe concluir la implementacion iniciada en la rama

add_new_model_resource

Queda pendiente:

* Los Webhooks no necesitan tener asociado un Data Type, en su lugar los webhooks pertencen a un Resource y el Resource tiene un data type.

* Los Webhooks no necesitan tener asociado un path, en su lugar los webhooks pertencen a un Resource y el Resource tiene un path.

* Crear el Script para la migracion de los datos.

### 30. Crear el Shared Collection de Cenit a partir del spec en el directorio de Guru API. [Mary]

Actualizar el script que lee las especificaciones del directorio de Guru API que ya incluyen el spec de Swagger de Cenit IO y generar el Shared Collection de Cenit, con la misma logica que se genera cualquier otro spec.

### 28. Crear una integracion de Magento basada en el Swagger. [Mary]

El Swagger de Magento y fue adicionado al directorio de Guru API, de modo que debemos actualizar la sincronizazcion de las shard collections para poder adicionar el shared collection de Magento a Cenit basado en esa spec. 

Hacer un pull request a Guru  API annadiendo a la spec los temas de seguridad con OAuth 1 que soporta Magento.

Posteriormente agregarla a las Integraciones disponibles para Odoo.

### 27. Crear Integracion para Spree Ecommerce. [Mary]

Es importante trabajar en esta integracion con Spree. Es una tegnologia que dominamos y podemos tener potenciales clientes. Hay muchas pruebas que podemos realizar con Spree, similares a las que realizamos para Odoo.

ver tareas: 46, 45 y 2

### 26. Permitir importar diferentes tipos de API Spec. [Mac] 

Permitir importar diferentes tipos de especificaciones formales de API:

* Swagger
* RAML
* I/O Docs
* Google Discovery
* WADL, 
* API Blueprint

Esta tarea esta inciada por parte de Mary, pero esta pendiente de revisar a partir de los ultimos cambios que se han realizado en Cenit.

Para la transformacion a Swagger se uso 

- https://github.com/APIs-guru/api-spec-converter

### 24. API Connection ⇔  Swagger Spec [Pacheco]

La propuesta es que un Swagger Spec se pueda corresponder con un API Connection y sus conceptos relacionados de Resources y Webhooks

Revisar la siguiente presentacion para tener mas elementos relacionados con esta tarea

https://docs.google.com/presentation/d/1U7npFSNCPMDZDrDZyPNuP9blxEZmcxFGkDDvTFm2nqw/edit?usp=sharing

* Connectors
  * API Connections 
    * Resources
      * Webhooks

Lo que es lo mismo que:
* Webhook *belogs_to* Resource
* Resource *belogs_to* API Connection 

nota: el nombre de webhooks no es el mas apropiado, pero de momento seguiremos usandolo, se puede enteder como Metodo o Operacion e incluye la especificaicon del Metodo HTTP y ademas la posibilidad de especificar parametros.

En lo posible vamos a tratar de tener resultados parciales que podamos ir desplegando.

1. Tener una nueva accion (tag) que sea *Swagger*, que muestre la conversion a swagger del API Connection en modo de solo lectura. 

2. Mas adelante, debemos poder editar el Swagger y su edicion debe modificar la configuracion del API Connection correspondiente, o sea debe haber una sincronizacion entre el modelo API Connection (y sus referencias a Resources y Webhoks)  con el fichero Swagger.

3. Agregar a la vista del Swagger la opcion de visualizar el Swagger similar a Swagger Editor (http://editor.swagger.io/). Una variante es ver si es posible embeber el Swagger Editor en Cenit, en ese caso Cenit deberia tener una variable de configuracion con la URL de la aplicacion del swagger editor, si no se especifica valor, debe funcionar con fue descrito en 1) y 2).

### 23. Adicionar en el menú superior indicador para storages. [Aneli]

Cuando se esta logueado se muestran los monitors en ese grupo esta pendiente por adicionar a los storage.


### 21. Activar el modelo de Confirmable. [Mac]

Para poder activar el modulo confirmable es necesario migrar los datos y a todos los usuarios existente asignarle a confirmed_at  Date.today-1 

### 20. Mejorar y expandir el uso de los tags. [Aneli]

Los tags fueron adicionados por Daniel para los Algoritmos. Pero usan la interfaz por default de rails_admin para las relaciones Many to Many con dos text area uno al lado del otro, donde es posible seleccionar los tag y pasarlo a la otra area..

1. Mejorar la interfaz de los tags, para que sea un imput de múltiples tag con autocompletamiento. Revisar las librerias de JQuery existentes.

2. Adicionar los tags a otros modelos como las Collecciones y los Shared Collections, revisar que otros modelos se pueden beneficiar de esto, pero la intencion es que sea un patron que podamos relacionar con todos los modelos que necesitan funcionalidades que faciliten el *discovery*.





### 16. Adicionar estadisticas de los monitors en el dashboard. [Mac]

En el dashboad se muestran 3 rectangulos con los *monitors*:

* running task
* autorizactions
* notifications

Cada uno debe mostrar la cantidad correspondiente. Esto cuando se este logueado y cuando no.

### 15. Push asincronos. [Mac]

Un push a Cenit mediante el API debe ser procesado de forma asíncrona, en el momento del push se debe retornar el *id* de una Tarea, de modo que posteriormente se pueda revisar el estado de la ejecución de la tarea.
Por ejemplo la tarea que se retorna asociada a un push puede estar relacionada con otras tareas.

Una tarea puede generar otras subtareas y se necesita recuperar ese arbol de dependencias para poder saber si todo se termino correctamente

### 14. Permitir múltiples usuarios por cuenta. [Mac]

Ya esta implementado la logica para poder tener multiples tenants por usuario, queda pendiente permitir múltiples usuarios por tenant.

Se debe tener al menos dos roles dentro de account, el role de  owner de la cuenta y  una con otro Rol (que en el futuro limite por ejemplo la vista de factura, o de adicionar usuarios y cambiar los roles dentro del tenant, etc)

El rol Owner tendria acceso en  el dashboard al area de administración

### 13. Revisar solapamientos entre Tenant y Namespace y entre Collection y Namespace. [Mac]

El Namespace como elemento base de los shared cross: 

Con la idea de simplificar toda la gestión de los namespace y su repetición en todos los formularios, podemos revisar la posibilidad de unificar los conceptos actuales de Tenants y Namespace siguiendo un poco el estilo de Github con las Organizaciones.

Cuando uno se crea una cuenta en github, tiene por una especie de ‘organización por default’ asociado al user_name, luego tiene la posibilidad de crear nuevas Organizaciones. Las Organizaciones hacen la funcionalidad de gestión modular, similar a la de un namespace, cada repo queda asociado a una organización (o la que llamamos organización por default del usuario). Esta lógica de Organización en Github permite además gestionar permisos y asociar usuarios, define el acceso por API. Cuando a un repo se le hace un fork, se puede decir que es equivalente a cambio de namespace.

Si unificamos en cenit los conceptos de Tenant y Namespace, podemos quedarnos solo con Tenant, manteniendo la lógica actual de crear un tenant por default asociado a una nueva cuenta, y luego se da la posibilidad de crear nuevos tenant. Si el tenant a la vez lo entendemos como un namespace, no es necesario en cada formulario tener un campo que especifique el namespace. Esto junto con la nuevas opciones de la UI que simplifican la forma en que se cambia de tenant a otro debe hacer que queden mas intuitivas y fácil estos conceptos a los usuarios.  

 Cuando a un Shared Collection se le haga pull, sería una especie de ‘fork’ quedando el collection dentro del namespace especificado por el tenant.

Por último en cuanto agreguemos la posibilidad de subdominio podemos, asociar cada tenant a un subdominio de cenit, con lo que la funcionalidad multi-tenant debe quedar mas explicita. 

El namespace como funcion de modularidad:

Otra pregunta podria ser: "Si ya tenemos el concepto de Collection para que necesitamos los Namespace?"

En cuanto a la logica actual, donde el namespace es lo que permite identificar que los diferentes modelos son relativos a un mismo Collection como Facebook, creo podemos usar el name de collection para sustituir ese uso de los namespace. Cualquier modelo nuevo que se cree podria pertener a un Collection. Cuando tengamos implementado el menu de Objetos, el primer nivel de navegacion podria ser el Collection, revisar la propuesta del menu lateral de objetos en esta presentacion (https://docs.google.com/presentation/d/1U7npFSNCPMDZDrDZyPNuP9blxEZmcxFGkDDvTFm2nqw/edit?usp=sharing) 


### 12. Usar las URL con Slug como URL predeterminada en lugar del ID. [Mac]

Ya en Cenit se soportan las URL con Slug y ademas de las id -que son la URL que contruye Rails Admin por default-, en adicion seria conveniente que las url predeterminadas en la documentacion sean con slug. Esto ademas ayudaria a que sean indexadas por los motores de busqueda.





### 9. Cambiar el nombre del modelo Account por Tennant. [Mac].

Ahora en Cenit es posible tener asociado a un usario varias "Accounts" con lo cual es mejor renombrar el concepto de "Account" por "Tennant" 
 
### 5. El email y el pdf de OSSE no soporta tildes. [Mac]
 
Al parecer porque es UTF-8, hay que revisar la posibilidad de seleccionar el enconde



### 3. Subdominios para las aplicaciones. [Pacheco]

Para que las aplicaciones tegan mayor valor de uso, es importante que se pueda asociar un dominio o subdominio propios.

- www.userdomain.com
- www.sub.userdomain.com

Para esto debemos desplegar las aplicaciones en un sudominio de cenit.io, preferentemente generado alearotiamente, de modo que no tengamos colisiones con los subdominios que deben ser reservados a cenit. Ejemplo

- https://polar-wave-7672.cenit.io

Para esto tenemos que asociar un certificado wildcard con el dominio cenit.io

Hay que ver como es posible configurar Nginx para que dinamicamicamente pueda responder a estos dominios o subdominios propios

Por ejemplo para una web como mytriptomoon, podria tener una aplicacion para la autenticacion con varios provedores de identidad usando cenit, que desee que se visualice en:

https://signin.mytriptomoon.com


### 1. Algoritmos remotos. [Pacheco]

**Cenit Algorithms**

La posibilidad de definir algoritmos es una de las principales funcionalidades que tenemos en cenit.

Tenemos dos limitaciones principales:

* hoy solo podemos definir codigo ruby (en particular, seria conveniente tener Scripts en JS que es mas universal)
* seria conveniente poder adicionar bibliotecas (en el caso de ruby serian gemas)

Lo mas importante es que para cada uno de esos leguajes  podemos manejar referencia a las bibliotecas  correspondientes de cada lenguaje. Lo cual daria un salto significativo a lo que se puede expresar con una algoritmo. Practicamente 'cualquier cosa', porque una biblioteca puede tener previamente programado funcionalidades que es casi imposible programarlas desde cero mediante el metodo actual.

Podemos usar un enfoque similar al proyecto open source Morph 

https://github.com/openaustralia/morph  

el sitio oficinal del proyecto es 

https://morph.io/

La documentacion se puede revisar aqui.

https://morph.io/documentation

Como logra morph manejar esos lenguajes y ademas gestionar la posibilidad de incluir bibliotecas.

La funcionalidad esta desarrollada sobre un proyecto open source de heroku, que son los Buildpacks, heroku tiene    Buildpacks por default para los principapes lenguajes de programacion que soportados oficialmente por heroku, y ademas hay collecciones de Buildpacks customizadas hecha por la comunidad.

Los pasos serian, 

* probar morph con el sitio
* revisar el codigo de morph
* familiarizarnos con Buildpacks
* tener un server que nos permita correr los builpacks

En ruby por ejemplo, ademas del script lo unico adicional que debemos definir es un Gemfile y Gemfile.lock y luego debe funcionar

Esto ademas termina de redondear la potencialidad del concepto de aplicaciones en Cenit, con esto una applicacion en Cenit, puede ser completamente equivalente a una app en sinatra (incluso mas adelante posibilitando el acceso a una db). 

En una 2da etapa cuando tengamos funcionando la alternativa de morph, podemos evaluar correr los buildpack sobre Dokku.

Dokku es una variante open source ligera de heroku, se llama Dokku. 

Dokku tiene un deamon. Seria trabajar en un api para dokku. Donde se pueda hacer un despliegue de una app programaticamente

Aunque el condigo de Morph incluye la logica para poder correr los buildpack, parece que es mejor opcion hacerla sobre Dokku, es una comunidad mas activa, y el alcanse del proyecto, es mas general ya que no se limita solamente a los scrappers. Pero podria ser una 2da etapa, luego de tener algo funcional con la variante de Morph.

En Cenit podemos pensar en dos tipos de algoritmos, local or remote, 

Los algoritmos locales: son los que tenemos actualmente, tiene full acceso a la bd de cenit, de momento solo soportados en ruby, y no permiten referencias a bibliotecas. Deben poderse ejecutar de forma sincrona o asincrona

Algoritmos remotos: la comunicación con cenit sería mediante el api, y debe ser programada, soportados múltiples lenguajes mediante la tecnología del buildpacks de Heroku, permiten incluir referencias a bibliotecas. Deben ser siempre ejecutados de forma asíncrona.

Cada ejecución del algoritmo debe ser representada por una tarea asíncrona en Cenit.

De forma opcional el output es definido por un DataType. Cada ejecución del algoritmo puede tener un set de objetos del data type (con cenit, pueden ser exportados como JSON, XML, CSV, etc)


**Algoritmos remotos**

Un algoritmo por default no tendría nada para la comunicación con los modelos de Cenit. Pero para lograr esto, podemos en el template (un gist) agregar una secuencia de pasos comentados, que permitan leer los parametros del algoritmo desde cenit, mediante un push (HTTP Post) retornar el resultado del algoritmo a cenit.

Del mismo modo puede estar comentadas otras operaciones con el API de cenit. En caso que se desee leer objetos del setup(conectores, tareas etc)

Por ejemplo el template para ruby, tendría el Gemfile, Gemfile.lock y un algorithm.rb, un template similar al que crea morph.io, por ejemplo:

- https://github.com/sanchojaf/city_test3/blob/master/scraper.rb

Como el algoritmo puede ser público es importante que las credenciales se suban al buildpack como variables de ambiente.

Input

```bash
curl GET -H "X-User-Access-Key: N63563526" -H "X-User-Access-Token: TYQTWY454521QQ12" \
https://www.cenit.io/api/v1/algo/#namespace/#algo_name/input
```

Json 

```Json
-> {
    "input": ["transformer","retransform"],
}
```

Output

```bash
curl -H "Content-Type: application/json"\
     -H "X-User-Access-Key: N446264203"\
     -H "X-User-Access-Token: 5T6YJqGYJgE5cULq6WQ_"\
     -X POST -d '{“output": json_result}'\
     https://www.cenit.io/api/v1/algo/#namespace/#algo_name/output
```

Con ejecución del curl anterior desde el algoritmo, podemos en cenit, garantizar que el algoritmo esté asociado con cada uno de los output. (mostrándolo similar a como lo hace cenit)

Del mismo modo el algoritmo puede realizar un push a cualquier otro modelo de cenit, o invocando otras acciones del API de cenit.


En función del lenguaje que se seleccione para el algoritmo, pondremos una alternativa de curl para el lenguaje específico (Ruby, Python, Node.js), por ejemplo en el caso de Python algo como.


Version de python

```Ruby
import json,httplib
connection = httplib.HTTPSConnection( https://www.cenithub.com/api/v1', 443)
connection.connect()
connection.request('GET', 'algo/#namespace/#algo_name/input', json.dumps({
       "input":  ["transformer","retransform"],
), {
       "X-User-Access-Key": "${APPLICATION_ID}",
       "X-User-Access-Token": "${REST_API_KEY}",
       "Content-Type": "application/json"
     })
result = json.loads(connection.getresponse().read())
print result
```



####################################################################################################

# done

- Pacheco: 40, 25

- Mary: 55, 48, 32, 50

- Aneli: 42, 6, 19, 38, 4, 18, 17, 11, 10, 23, 67, 22, 65, 68

- Mac: 2, 8, 35, 49, 7

### 68. ~~Vistas de index embebidas deben mostrar las acciones con los 3 puntos verticales~~. [Aneli]

En las vistas de index embebidas como la que se usa en el show de los cross_shared_collections, las acciones asociada a cada fila, se deben mostrar con los 3 puntos verticales, de modo que sea uniforme con el resto de la plataforma.

En caso de la accion Filters, revisar como se puede convertir en una vista embebida, e igualmente mostrar las acciones.

### 65. ~~En 'send to flow', mostrar la tabla o la cantidad de elementos a los que aplica~~.  [Aneli]

En la accion send to flow es conveniente que se mueste debajo la tabla de los elementos a los que va a aplicarse la accion.

En caso qeu la tabla no sea lo mejor, mostrar la cantidad de elementos.

Esto es para evitar que una accion de flow se aplique a elementos que no se desea. 

Pensar ademas como mejorar el siguiente escenario.

Cuando usuario marca algunas filas y luego va directamente a 'send to flow' en lugar de tomar las filas marcadas, se toman todas las filas, ya no se uso la accion 'Selected Items', seria bueno mejorar la experiencia de usuario en este caso, quizas mostrando un warning, o seleccionando los elementos marcado que una opcion para seleccionar todos si era la intencion.

### 22. ~~Limitar el listado de acciones a 2 y luego un boton que diga 'Actions'~~. [Aneli]

En las paginas de index, adicionar un boton 'Actions', inmediatamente a la derecha de 'Add New', o se tendriamos, 'List', 'Add New' y luego 'Actions'

Este boton debe permitir desplegar el resto de las acciones.

En las otras vistas que no son Index aplicar una logica similar.

### 67. ~~Mejorar la URL predeterminada de los Object Types~~. [Aneli]


La URL actual de los Object Type, luce como esta

	http://localhost:3000/dt581c7a75334c4a68d5000006

Esa URL corresponde al object type:  'Basic | OrderTotals'

La url deberia ser similar a la que usamos en el api
	
	http://127.0.0.1:3000/api/v2/basic/order_total
	
, o sea la URL en el admin, deberia ser:

	http://localhost:3000/basic/order_totals

Por ejemplo los modelos de Ecommerce, deben quedar como 
	
	http://localhost:3000/ecommerce/orders


Usar '/' para separar el namespace del nombre

deria sera
    
    Ecommerce / Orders

### 23. ~~Adicionar en el menú superior indicador para storages~~. [Aneli]

Cuando se esta logueado se muestran los monitors en ese grupo esta pendiente por adicionar a los storage.


### 10. ~~Redireccionar los link de notificaciones a filtros~~. [Aneli]

En el menu superior aparece un icon de las notificaciones y asociado con el icon diferentes numeros relacionados con el tipo de notificacion, cuando se le da click a uno de los numeros esta redireccionando a las notificaciones, pero no a las notificaciones filtradas por el tipo de notificacion del numero.

### 11. ~~Eliminar ‘setup~’ prefijo de las url.~~ [Aneli]

Todas las url tienen el prefijo 'setup~' que lo toma rails_admin de la carpeta setup. eliminar este prefijo que no cumple funcion.

### 17. ~~En el Show de los Shared Collections incluir un link a la lista de todos los Webhooks~~. [Aneli]

Cuando un Shared Collections que tiene muchos Webhooks, en el Show aparecen listado solo una parte de los Webhooks. Por ejemplo en caso de Gmail, solo se muestran 35 de un total de 56. Sería conveniente tener un link que al darle click redireccione a la pagina donde se listen todos los webhooks que pertenecen al Shared Collection.

### 18. ~~Cambiar los has_many en los index mostrando solo los primeros elementos y la cantidad~~. [Aneli]

Cambiar la vista por default de index de rails_admin, para que las columnas que se corresponden con una relación has_many mostrando los 3 primeros elementos de la lista y luego un número con la cantidad total de elementos

### 4. ~~En todas las tablas sustituir el listado de acciones por 3 puntos verticals~~. [Aneli]

Similar la solucion que se hizo en la tarea #38 para dashboard 

En el listado de acciones, que han ido creciendo con el tiempo. La propuesta es sustituir este listado de acciones por un icon de 3 puntos verticales, que al dar click despliegue un menu con el listado de acciones correspondientes, pensar ademas como mostrar como un subnivel si una apcion se define como un pop-up.


### 2. ~~Agregar a la navegacion Ecommerce~~. [Mac]

Las motivaciones de este cambio son para hacer mas evidente las posibilidades que tiene Cenit para el mundo Ecommerce. Cenit es una plataforma genérica de integración, y técnicamente las funcionalidades para el tema ecommerce son similares a otros dominios de aplicación, pero es importante diferenciar este segmento. 

En el menu de navegacion ya tengamos explicitamente un item para Ecommerce, y como elementos de segundo nivel tendriamos: Customers, Products, Inventory, Cart, Orders, Shipments. 

Los modelos de ese namespace estarian pre-instalados en cada nuevo tenant que se lance y su definicion debe corresponder al repo (https://github.com/cenit-io/ecommerce)[https://github.com/cenit-io/ecommerce] 

* Ecommerce
  * Customers
  * Products
  * Inventory
  * Carts
  * Orders
  * Shipments

Aunque se permitia cargar otros modelos tendriamos una biblioteca "oficial" de Ecommerce, de modo que siempre que los modelos sean algunos de los oficiales se pueda sacar provecho de ello y contar con funcionalidades Out the box para estos modelos.

Es importante notar que MondoDB permite que cuando persista una orden en particular, pueda tener tener campos dinamicos, o sea atributos adicionales a los especificados originalmente en el modelo, lo que brinda flexibilidad a los mapeos, de hecho esos atributos dinamicos pueden ser incluso anidados.

En los SDK que desarrollemos podemos tener facilidades para el push de estos modelos hacia Cenit. O una plataforma ecommerce como Spree o Magento, puede tener una extension para la sincronizacion de estos modelos. Por ejemplo cualquiera de estos Store, con una extencion puede implementar una logica de push automatico que se ejecute automaticamente que se cree una nueva orden, lo cual tiene ventajas a la hora de lanzar eventos sin que se tenga que esperarar por una instancia del scheduler periodico cada 20 minutos.
Veamos algunos ejemplos:

En el caso de Sathechi, las ordenes de cada uno de los marketplace es traducida a los Shipments de Shipstation.
lo ideal es que exista integraciones de:

- Order Fancy <-> Order Ecommerce
- Order OverStock <-> Order Ecommerce
- Order Shipstation <-> Order Ecommerce

La ventaja de este enfoque es que cualquier funcionalidad que se haga a partir de Order Ecomerce queda disponible por transitividad para todos los modelos Order que sean posible transformarce en Order Ecommerce.

Escenario 1:

Si de momento en lugar de enviar a Shipstation, lo que interesa es hacer el envio a Shipwire, el esfuerzo se debe reducir a transformar la Order (o el Shipment de Shipwire) en la Order de ecommerce

Escenario 2:

Si tenemos una funcionalidad que a partir de un Order se genere un Invoice pdf con un template prawn
Aunque del punto de vista de implementacion, no debe cambiar mucho, ya que deben ser modelos que se carguen dinamicamente, el hecho de que tengan una UI propia, permite agregar actions que se puedan visualizar desde el mismo dashboard.

Podriamos tener en el API una descripcion explicita para estos modelos, de modo que la curva de aprendizaje para que alguien logre subir una Orden a Cenit sea menor.

ver tareas: 46, 45 y 27

### 55. ~~Publicar shared collections de Store~~. [Mary]

Es importante poder publicar todas las shared collection de Store que sea posible, aunque la implementacion del API no sea completa.

* Houzz
* Walmart
* Odoo
* Magento

### 42. ~~Mejorar la interfaz de los wizards~~. [Aneli]

Los Wizard debemos usarlo solo donde sea impresindible, ya que se aleja de la forma comun de los EDIT que es la propuesta por RailsAdmin.

Donde se justifique el uso de Wizards podemos mejorar la forma en que lo estamos presentando.

- Es conveniente tener un nombre por cada paso, 
- que pueda mostrar los pasos (arriba o abajo)
- que se muestre cual es el paso activo

En este link se puede ver un ejemplo:

- https://drive.google.com/file/d/0B-ltzH-m3LxTZXpvaFM4N18xZUk/view?usp=sharing

### 40. ~~Accion que genere cURL para acciones que existen en el API~~. [Pacheco]

Similar a algoritmia.com, que tiene varios link para usar la api según el sdk, de momento para nosotros es suficiente con tener cURL, la idea es tener una accion en el admin de cenit (para aquellas accionees que corresponden a metodos que existen en el API), donde al dar click la accion aparezca el codigo cURL y se pueda copiar y pegar en una consola y funcione, para esto el curl incluira las credenciales correspondiente al tenant.

Por ejemplo vean el curl en

- https://algorithmia.com/algorithms/nlp/Summarizer

```shell
curl -X POST -d '<INPUT>' -H 'Content-Type: application/json' -H 'Authorization: Simple YOUR_API_KEY' https://api.algorithmia.com/v1/algo/nlp/Summarizer/0.1.3
```

### 19. ~~Mejorar el tour~~. [Aneli]

Del tour se hizo una primera implementacion en el portal anterior de Cenit por parte de Daniel, se puede ver aqui

- https://cenit-portal.herokuapp.com/

Y en repo

- https://github.com/cenit-io/cenit-portal

Luego esa implementacion se paso ha Cenit, se puede ver un link en el menu lateral derecho, pero en estos momento no esta funcional.

La propuesta es ir abriendo los elementos hojas del sidebar lateral de navegación, e ir expandiendo los niveles y colapsando en la medida que el tour avanza.


### 6. ~~Mejorar navegación e interfaz de las Transformaciones~~. [Aneli, Mac]

Las transformaciones es uno de los conceptos principales que hemos desarrollado y en expresividad es comparable con los algoritmo u otros conceptos que tenemos.
Aun pueden ser usado como una parte impotante en los Flujos, la idea es que tengan valor en si mismo, y puedan ser usando de forma independiente.

I ) Incluir este concepto como un primer nivel en la navegación

* Transformations 
  * Render (type exporter)
    * HTML (html.erb, liquid)
    * JSON (json.rabl)
    * XML (xml.rabl, xslt)
    * JS (js.erb)
    * PDF (pdf.prawn)
    * CSV (csv.erb)
    * Text (txt.erb)
  * Parser (type importer)
  * Convert
  * Updater

IV) Mejorar la UI a partir del hecho que cada una corresponderá a un tipo particular de transformations  a diferencia de como estábamos trabajando hasta ahora.

III) Incluir la ventana de test que se implemento al principio

### 7. ~~Los Récords por default deben ser visibles en la navegación~~. [Mac]

I)  En lugar de tener *Records* en la navegación sustituirlo por dos conceptos *Objects* y *Files*, correspondiendo a *JSON Data Types* y *File Data Types* respectivamente.

II) Cuando no se este logueado que puedan aparecer *Objects* y *Files*.

III) Debajo de *Objects* un action que sea 'link a JSON Data Type', y debajo de Files un action que sea 'link a File Data Type', se mostraria tanto cuando se este logueado que cuando no se este logueado, de modo que se pueda usar como parte del tours, cuando se este logueado si aparecen mas sub-niveles, siempre la accion seria el primer elemento en la lista de sub-niveles.

### 8. ~~Definir un Segmento en los Datos asociado a un Data Event.~~ [Mac]

Por ejemplo si se define un evento de Placed Order para las ordenes con status Placed
Que automáticamente en la navegacion del menu lateral se cree un subnivel para Placed Orders

Donde podamos inspeccionar este subconjunto de las ordenes, y tenga solamente los flujos asociados con ellas (en caso que existan flujos definidos)

Una misma orden puede estar en varios segmentos.

### 48. ~~validar la rama snippet_code con las cosas de OSSE.~~ [Mary]

Esta nueva rama snippet_code tiene cambios de fondo que debemos revisar bien con las coass de OSSE y Satechi, para evitar romper algo en produccion.

### 50. ~~Validar la herramienta cenit2odoo~~. [Mary]

Pacheco hizo una reimplementacion de a la herramienta de generacion de addons de Odoo a partir de un shared collection en Cenit.

Revisar en detalle la generacion de los addons y compararla con los que estan actualmente.

Abajo una primera prueba con twitter, para comprobar el resultado de la generacion automatica, se puede ver en una nueva rama compare_auto_generate_twitter_integration del repo de cenit-io/odoo-integrations, la comparacion de esa rama con la version 9.0 se puede ver en el siguiente link

https://github.com/cenit-io/odoo-integrations/pull/16

Se puede ver las diferencia, es importante notar que este twitter original se le hizo ajustes manuales, con lo cual no podemos esperar que todo este en la generacion automatica, pero si ver de las cosas que no estan que otra cosa puede ser generada a partir de la informacion que hay en el shared collection de cenit.

https://github.com/cenit-io/odoo-integrations/pull/16/files?diff=split

Lo mas importante a revisar son las cosas que se eliminan en el pull request, o sea todo lo qeu esta en rojo, porque no fue generado automaticamente.

Ademas aparecen algunos comentarios.

Lo mismo de Twitter esta para shipstacion, en la rama

compare_auto_generated_mailchimp_integration

el diff se puede ver en 

https://github.com/cenit-io/odoo-integrations/pull/17/files?diff=split

### 38. ~~En el dashboard sustituir el listado de acciones de cada modelo por 3 puntos verticals~~. [Aneli]

En el dashboard asociado con cada modelo, aparece el listado de acciones, que han ido creciendo con el tiempo. La propuesta es sustituir este listado de acciones por un icon de 3 puntos verticales, que al dar click despliegue un menu con el listado de acciones correspondientes.

### 25. ~~Usando el API de Cenit generar los modulos de integracion de Odoo.~~ [Pacheco]

Actualmente en Cenit tenemos mas de 2270 integraciones, de estas integraciones unas 10 las hemos adecuado a modulos de integracion Cenit Odoo, lo cual permite a Odoo integrarse con terceros sistemas a traves de Cenit.

La mayoria de los clientes que han llegado a Cenit han sido a partir de conocer estas integraciones en Odoo.

En esta URL se pueden ver los modulos publicados en Odoo Apps

- https://www.odoo.com/apps/modules/browse?search=cenit

Daniel incio un proyecto en Python que de forma programatica permite generar un addons de Odoo correspondiente a un shared collection en Cenit.

- https://github.com/cenit-io/odoo-cenit-collection-bundler

Esta generacion automatica se puede hacer a partir de la informacion que se obtiene de Shared Collection a traves del API. El proyecto no se ha actualizado en mas de un anno, durante ese tiempo se ha modificado el API.

En este repo estan los modulos actuales de las integraciones en Odoo.

- https://github.com/cenit-io/odoo-integrations

Por ejemplo, la integracion particular de Twilio, se puede encontrar en

- https://github.com/cenit-io/odoo-integrations/tree/8.0/cenit_twilio

y es un sub-directorio con la siguiente estructura

- cenit_twilio/
  - models/
    * __init__.py
    * config.py
  - secuirity/
    * ir.model.access.csv
  - static/
    * description/
      - index.html
      - ...
  - view/
    - config.xml
    - wizard.xml
  - __init__.py
  - __openerp__.py

### 32. ~~Actualizar la pagina actual de la documentacion del API.~~ [Mary] 

Actualizar la documentacion del API, en correspondencia con el Swagger.

La URL de documentacion del API es:

- http://cenit-io.github.io/docs/api/

La URL del Swagger es:

- https://cenit.io/openapi/v1/swagger.json

Para actualizar la pagina de documentacion se debe modificar dos ficheros JS:

- https://github.com/cenit-io/docs/blob/gh-pages/api/api_project.js
- https://github.com/cenit-io/docs/blob/gh-pages/api/api_data.js

Esta actualizacion debe ser temporal porque debemos lograr que la pagina de documentacion del API se genere automaticamente a partir del fichero Swagger.

### 31. ~~Crear tarea que genere el swagger.json a partir del swagger.yml~~ [Mary]

La generacion del swagger.json debe ser programatica de modo que cada vez que se modifique el swagger.yml sea posible ejecutar un *rake task* como

    rake openapi:ymltojson

Que lea el yaml:

    /public/openapi/v1/swagger.yaml

y sobreescriba el json:

    /public/openapi/v1/swagger.json
    
### 29. ~~Probar y actualizar las integracion de Cenit con Odoo 9~~. [Mary]

Instalar Odoo 9 y probar cada una de las integraciones con Odoo 9.

Como parte de la actualizacion revisar la documentacion.

### 35. :bug: ~~Cenit local no esta salvando correctamente los objetos.~~ [Mac]

En mi instancia local de Cenit, cuando creo los namespace no aparecen luego en el listado del index

Lo mismo me paso creando un JSON Data Type, cuando doy save aparentemente salva satisfactoriamente, pero luego el listado aparece vacio.

Cree una cuenta nueva y paso lo mismo, previendo que mi cuenta estuviese corrupta.

### 49. ~~Actualizar los conceptos que aparecen en el API.~~ [Mac]

La documentacion del API esta publica en 

https://cenit-io.github.io/openapi/

lo que corresponde al repo de github 

https://github.com/cenit-io/openapi

Ahi cada concepto tiene una definicion, que se debe actualizar.

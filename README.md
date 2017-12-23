# errores/mejoras

- [new] en las trazas del dashboard cuado se da click en more, una alternativa es cargar una cantidad adicional y mostrar un scroll, y asi sucesivamente.

- [new] cuando se cambia la estructura de un datatype, luego no se pueden realizar las acciones de eliminar o editar los records que estan con la vieja estructura del mismo datatype, se ve el record en el show y en el formulario de editar, pero cuando se realizan los submit(delete|edit) Cenit da error... sin embargo por el api si se permite realizar estas acciones.

- [new] valorar en el menu de navegacion general izquierdo, que tanto el icon como el nombre del subdominio puedan ser clicleable y redirigir al dashboard de ese subdominio.

- [new] Known critical severity security vulnerability detected in nokogiri < 1.8.1 defined in Gemfile.lock.

- [new] Al activar un flow compartido, despues de ejcutarlo, vuelve a desactivarse.

- [new] Valorar,  dejar estático la parte de las acciones en los formularios, y en el caso de los vistas index ademas  dejar estático la primera fila de los nombres de las columnas.

- [new] en el dashboard donde aparecen las trazas,  valor tener un tab por cada origin, asi por ejemplo serias mas sencillo distinguir la actividad de los cross shared, de las actividades propias del tenant.


- [new] En el Dashboard, usar solo los numeros en rojos, para cosas negativas, ejemplo: running task failed o Authorization Unauthorized. Pero no usarlo para cosas como el numero de un data types.

- [new] cuando se ejecuta en el search box de un data type, aparece en la parte inferior un `loading...` seria  bueno ver si se puede mostrar este `loading..` siempre que cenit este cargando una pagina, o sea tratar de extenderlo a otros casos.

- [pendig] Permitir en algunas cuentas que el hitorial de notifaciones se de mas tiempo, en particular las cuentas de clientes como OSSE, seria bueno tener notificaciones de al menos 30 dias, ahora  solo tienen dos dias de antiguedad.

# backlog

### 103. backup y restore a nivel de tenant.

Algo que podria ser bueno es poder  hacer backup y restore a nivel de tenant, pensando en clonar con la idea de ambientes de test y produccion, cenit remotos, etc

Se podrian tener politicas de respaldo de los datos por tenant
y cobrar el store, no se

a mi (Asnioby) me gustaria poder hacer un backup de lo que tengo en un tenant de cenit y despues un restore en un cenit local Quizas no es tan simple pero como idea se puede pensar un poco


### 102. Sincronizar los shared collections y collections con un repo de gitlab. [Mac]

Cuando las integraciones son grandes se hace complejo poder seguir la evolucion de los cambios, revisar el historial, y auditar quien hizo el cambio.

cuando hemos tenido errores por ejemplo een las cosas de OSSE, siempre tenemos la duda si pudo ser un cambio que se hizo por parte del equipo de OSSE.

Hay un modulo de audit que tenemos pediente extender y que puede en alguna medida ayudar a monitoriar los cambios. 

Pero en el caso de los Shared Collection y las Collections lo ideal es poder sincronizar con un repo.

Si contamos con una `version oficial` del JSON Schema de una Colleccion, podemos sincronizar los shared collections y los collections, con un gist de github, los shared collections con un gist publico, y los collections con un gist privado.

Una variante mas avanzada es poderlo sincronizar con un repo git, donde podriamos utilizar Gitlab, esto tendria otros beneficios extras:

- gitlab soporta repos publicos y privados,

- seria facil comparar usando las funcionalidades del git las versiones de la coleccion.

- se podria definir con que rama trabajar, de modo que si alguien esta haciendo un trabajo complejo, podria cambiar entre una rama master, test o develop donde se puedan probar funcionalidades.

- del mismo modo se podria revertir los cambios e ir a una version anterior.

- del lado de cenit, cuando se haga un cambio en un elemento que pertenezca a una colleccion, eso podria disparar una tarea que se engargue de subir el cambio correspondiente, a la rama asociado con la colleccion.

- seria mas sencillo el proceso de hacer un clone a una colleccion, cabiar algo e importarla como una nueva coleccion.

- persistir el shared collection mas alla de la base de datos, de modo que ante una situacion critica, se pierden los datos, pero la configuracion de la integracion se puede recuperar con el collection.

- Gitalab al igual que cenit puede ser intalado en una red cerrada, lo qeu puede ser una solucion atractiva en ambientes empresariales.


### 101. Paginas de Documentacion. [Mac]

Valorar mover el repo de documentacion, dentro del propio repo de Cenit, similar a como lo tiene gitlab, o spree.

Mantener la posibilidad de que las paginas de documentacion podamos continuar escribiendolas en Markdown. 

Podemos tener una primera version de documentacion, que sea al menos una pag por cada Subdominio: Data, Workflow, Gateway, Compute, Ecommerce. Pensar como y donde podemos mostrar los link de la navegacion para que sea parte inherente de Cenit y no algo externo, hoy tenemos un link en acciones.

### 100. Mejorar como presentar los Flows dentro del show de las shared collections. [Mac]

Algo mas simple que el trabajo en las nuevas aplicaciones, y que en alguna medida es posible aplicar a todas las  shared collection es que en el show sea mas comodo interactuar con los flows, donde se pueda activar o desactivar el flow (si es un flows de tipo scheduler qeu la accion de activar/desactivar se apique con una sola accion tambien al scheduler). O quizas en lugar de modificar en el show, sea una nueva action Flows

Quizas los flujos podemos presentarlos en dos bloques, uno los de data event, y otro los scheduler.

lo ideal es que para activar tengan algo asi como un interruptor.

En lugar de la tabla por default actual del show quizas se puede mostrar una tabla algo mas customizada. Y Ponerla en un lugar mas relevante justo detras del readme si en el show, o en un action aparte al show.

Si un action aparte en el shared collection puede ser un popup, con los flujos.

![flows](https://user-images.githubusercontent.com/4213488/31229162-a89d6c44-a994-11e7-8073-eebb30ba2d05.png)

Lo bueno es que si este cambio mejora la usabilidad podemos aplicarlo a todas las shared collections.

### 99. Integracion especial con las APIs que tienen webhooks.

Con estas APIs podriamos tener actualizaciones en cenit en tiempo real, con lo cual deben tener un tratamiendo diferenciado.

algo similar hacer en integrator.io.

este es un articulo viejo de programable.web donde se listan APIs que implementan webhooks

- AciveCampaign
- Aha!
- Assembla API: Online project collaboration service
- Atlassian Bitbucket API: Online distributed version control service
- Box
- Dispatch API: Event automation service
- Dropbox
- Errorception
- Facebook API: Social networking service
- Facebook Real-time Updates API: Real-Time Updates from Facebook
- GitHub API: Source code repository
- Google App Engine API: Developer platform
- Google Buzz API: Social sharing service
- Help Scout
- Human.io API: Micro-Apps for Android and iOS
- IMified API: Instant messenger buddy
- Intercom
- Inflectus API: Webhooks implementation service
- Instagram Real-time API: Real-time image sharing service
- Jira
- Kynetx API: Event-driven application platform
- MailChimp API: Email List and Campaign management service
- Metwit Weather and Forecast API: Real-time crowdsourced weather application
- Mozes API: SMS messaging service
- PagerDuty
- Papertrail API: Hosted cloud log management for server and app logs
- Postmark
- OpenMedia.io API: Entertainment content service
- PayPal API: Online payments
- Podio API: Online workplace platform
- RequestBin API: HTTP request analysis service
- Scalr API: Cloud hosting platform
- Segment
- SendGrid API: Cloud based email service
- Shopify API: Online shopping cart service- 
- Signal API: Interactive mobile and email marketing platform
- Slack
- Stripe API: Online payment service
- Surveygizmo API: Online survey service
- Torpio API: Cloud Application Extension Service
- Travis
- Twilio API: Telephony service
- UltraHook API: Webhook management service
- Wufoo API: Online forms creation service
- Zendesk API: Help desk service

### 98. simplificar como hacer una integracion entre dos aplicaciones.

ver este ejemplos

Integrator.io

https://www.youtube.com/watch?v=nu5PkSt9FkM

Stamplay

https://www.youtube.com/watch?v=UDC8oN9mtmc&t=10s

### 97. Crear un nuevo Data Type mediante una interfaz visual.

[Similar al desarrollo de Pacheco para OMNA]

En cenit podemos tener Field Types, que sean una extencion a los tipos que tiene rails admin, y que nos permitan en un editor crear un data type agregando los atributos, y por cada atributo, seleccionado el tipo. Es importante notar que un Data Type no es solo para definir el modelo para salvar en la base de datos, sino que tambien se genera la interfaz visual, de modo que si tenemos una manera visual de crear los atributos del Data Type podemos tener una semantica mas rica, para que la interfaz visual sea mas amigable, por ejemplo Password field, o Telephone field. Podemos ademas permitir que se definan nuevos Field Types(cada una estas extenciones debe quedar refresentado como un JSON Schema.)

Field Types: 

Text field, Password field, Text area, Telephone field, Url field, Email field, Number field, Range field, Date field, Time field, Datetime field, Month field, Week field, Check box, Radio button, Color field, Select box

Cuando el file type no corresponda con un file type basico de JSON Schema, entonces definirlo por detras como un JSON Schema.

Cuando se adicione un atributo, definir: 

- si es requerido o no
- si tiene valor por default
- place order.
- opciones si es un enumerator, etc.


ejemplo en Stamplay https://youtu.be/aG5HKecexs8

Adcionar la posibilidad de asociar el rich editor con un field en particular, preferentemente los text area.

### 96. UML to XML Schema(XSD).

XSD permite representar relaciones entre clases, y en Cenit se permite cargar un XSD y generar los modelos por detras.


La instalación de Generación XSD convierte un modelo de clase UML en un Esquema XML W3C (XSD). Esto permite empezar a trabajar a nivel conceptual en UML.

En esta misma idea, seria interesante poder tener un Editor de UML, que a partir de una presentacion visual de UML, genere todos los modelos y las asociaciones relacionadas.

En el link siguiente se describe una herramienta similar.

[reference](http://www.sparxsystems.com/resources/xml_schema_generation.html)

### 94. Integracion con Stripe. [Pacheco] 

Valorar la posibilidad de hacer un servicio indenpendiente a Cenit, realmente alquien que vaya a instalar un server local, no necesita conocer los detalles de como es la logica de cobro recurrente o los planes y precios. De modo que quizas lo mejor es crear un nuevo servicio para el tema del cobro y los planes, que mantenga un bajo acomplamiento con Cenit.

Sobre la lógica de suscripción con pagos recurrente la propuesta es seguir el proyecto de Rails Composer para Suscripción con Stripe.

Ver mas detalles en el reamde

https://github.com/RailsApps/rails-stripe-membership-saas


**Rails Stripe SaaS**

ensure that you have rails 4.2 like environment

`git clone git://github.com/RailsApps/rails-stripe-membership-saas.git`

`cd rails-stripe-membership-saas`

`bundle`

`rake db:migrate`

open Gemfile and add: `gem 'figaro'`

`bundle`

`rake db:migrate`

`vim config/application.yml`

add

```
STRIPE_API_KEY:  kkkkkkkkkkkkkkkkk
STRIPE_PUBLISHABLE_KEY: ffffffffffffffff
```

`rake db:seed`

`rails s`


### 93. Graphic Mapping Transformations

![graphic mapping transformations](https://user-images.githubusercontent.com/4213488/28247899-45ea812a-6a08-11e7-9010-6eba18dede10.jpg)

* Use an style similar to this project http://www.jsoneditoronline.org the source code is here https://github.com/josdejong/jsoneditor 

* Create one by one mapping

* Each map take several fields from the source json schema and define an optional handlebar expression

* The target json schema should be optional

* If the target json schema is present then validate the result with the schema.

* Advance option for auto-generate a mapping, maybe only for a subset of the fields, this feature require the presence of the target json schema.

* Auto-generate a complete JS Handlebars (read only)

* Validate Result with the target json schema.

* Generate a fake source data (similar to http://json-schema-faker.js.org/#gist/eb11f16c9edccf040c028dc8bd2b1756 )

* Allow load a json source.

References

SAP
![sap_2](https://user-images.githubusercontent.com/4213488/28248025-5d9df804-6a0a-11e7-829e-b539237bdfe9.png)
![sap](https://user-images.githubusercontent.com/4213488/28248026-5d9e522c-6a0a-11e7-81c7-0afb0da21850.png)
Altova
![altova](https://user-images.githubusercontent.com/4213488/28248027-5d9e6ce4-6a0a-11e7-95c4-f9cae6890f58.png)
Data Mapper Mulesoft
![data_mapper_mulesoft](https://user-images.githubusercontent.com/4213488/28248028-5d9ed422-6a0a-11e7-919c-4bc4b51fe1ca.png)
Json writer
![json_writer](https://user-images.githubusercontent.com/4213488/28248029-5da06c10-6a0a-11e7-9c04-3a74fb0e5614.png)


### 92. Adicionar NIMIO para la gestion de los ficheros estaticos. [Pacheco]

https://docs.minio.io/

demo: https://play.minio.io:9000/

### 91. Cenit Automation Email | Templates: Email, Spreadsheet , PDF. [Pacheco]


Una de las funcionalidades mas buscadas en las plataformas de Integración, como Cenit, que permite automatizar procesos de backoffice a partir de eventos en los datos, es la de Automation Email, sobre todo usado por marketing.

Básicamente como a partir de un evento, se puede enviar un template de email a uno o multiples usuarios .


 El correo que se está enviando en la integración que se le hizo a OSSE, cada vez que una factura es aprobada por la SUNAT hay varias cosas importantes.

* El template HTML que se usa, 
* Los datos generados en el cuerpo del correo
* los metadatos del email generados dinámicamente (como el from address)
* La autorización OAuth 2.0 con Gmail para que el correo se envíe desde la cuenta de Jose.
* El pdf adjunto generado con un template prawn.


Una de las funcionalidades mas buscadas en las plataformas de Integración, como Cenit, que permite automatizar procesos de backoffice a partir de eventos en los datos, es la de Automation Email, sobre todo usado para temas de marketing.

La idea es ver como extraer estas funcionalidades similares a las que se hizo para Jose, y presentarlas de una formas mas simple e intuitiva, además de agregar algunos templates. 

Podemos tomar como referencia a Mailchimp, Klavyo, tambien a 
https://www.zoho.com/invoice pero los pimeros templates puede ser mas sencillo que lo de un invoice.

Tenemos funcionalidades básicas, en el menú, los template aparecen ahora como Translations/Rederers

si puedes revisa cómo se implementó esa integración para OSSE, y trata de leer y revisar sobre Automation Email
para que revises si te parece factible
también hemos hechos desde cenit, email que en lugar de pdf, envían un csv como adjunto, el mismo google spreadsheets tiene templates de spreadsheet 

Para los templates del cuerpo de los  correos podemos buscar templates de email libres 
por ejemplo aquí

https://www.emailonacid.com/blog/article/email-development/600_free_email_templates


Tenemos que concebir el envío de los correos con los invoice que estamos preparando para OSSE como un flujo generico en Cenit.

Este es un caso de Uso muy interesante y puede interesarle a muchos usuarios.

En otros proyectos de los que he trabajado he visto todo el trabajo que se pasa para generar los pdf de los invoice.

En internet existen servicios como este https://www.zoho.com/invoice

Donde se puede seleccionar un template pdf de un invoice y se puede enviar el correo con el invoice adjunto, pero es limitado porque te permite seleccionar entre un número de template, y luego al template hacerle modificaciones genéricas, y ademas es solo para invoices 

Prawn
https://github.com/fadhlirahim/prawn-examples/blob/master/examples/invoice.rb

Pdf
https://github.com/fadhlirahim/prawn-examples/blob/master/examples/invoice.pdf


En nuestro caso una vez que tengamos el template generado con un prawn, podemos modificar cualquier cosa en el pdf, con lo cual es completamente customizable, pero además podemos generar otros documentos.

* Invoice
* Packing Slimp
* Gift Card 
* Tickets
* Boletos
* Codigos de barras.

Como en Cenit cada uno de estos elementos puede definirse como un Data Type, a partir del JSON se puede definir el translator (llamaremos mas adelante Transform) que convierte el JSON, en el pdf correspondiente.

La idea es que desde el API de cenit se pueda mandar a ejecutar el flujo del correo, especificando el Invoice, y como resultado llegue el correo con el Invoice adjunto.

Templates de Spreadsheets (que pueden ser adjuntados)

Google tiene los siguientes template de Spreadsheet.

https://docs.google.com/spreadsheets/u/0/?ftv=1&tgif=c#

Tienen templates en las categorías:

* Personal
* Work
* Education


Template PDF con prawn (que pueden ser adjuntados)

Extendí esta gema con el propósito de tener ejemplos sencillo de pdf


https://github.com/sanchojaf/prawn-examples

Es una manera fácil de probar las cosas offline 
antes de ponerlas en cenit, básicamente:

1- hacer clone a la gema

2- tener instalado `'prawn'` y `'prawn-table'` con
 
`gem install 'prawn'`
y
`gem install 'prawn-table'`

3- van a la carpeta examples y ahí a cada uno de los ejemplos

`cd examples/invocice_00`

son solo 3 ejemplo que van desde uno trivial a uno mas complejo,

4- si les parece cómodo pueden agregar nuevos ejemplos a la gema
prawn es el estilo que nos permite en cenit transformar el código ruby del translator en Pdf
Importante Cuando estén en la carpeta

`ruby invoice.rb`

Eso genera el pdf tomando como entrada el json de la carpeta


Referencias:

https://mailchimp.com/features/automation/

https://mailchimp.com/resources/guides/working-with-automation/html/

https://www.klaviyo.com/features/overview

https://www.zoho.com/invoice/tour/


### 90. Cloud functions y Celulas de Codigo de los Notebooks. [Pacheco]

Con la lógica de algoritmos remotos que se rabajo se puede hacer compatibilizar con los notebooks


Los Notebook tiene como elemento básico un ‘cell’


La Cell puede ser de documentación o un código, las células de tio codigo es bastante cercano a lo de los algoritmos remotos implementados por Pacheco.


Con esto además tendríamos la ventaja de la gestión de las bibliotecas que se trabajó para los algoritmos remotos, con lo cual podemos tener una mayor uniformidad entre las cosas de Notebooks y de los algoritmos remotos.


Con esto la ejecución de los notebooks podría ser  más eficiente porque tendríamos una app en heroku por cada lenguaje, como se hizo para los algoritmos remotos.


Mientras que en el caso de los algoritmos remotos si usamos la Células de Código de los Notebooks podríamos mejorar la interfaz, y la interactividad ya se podria ejecutar desde el mismo edit.


Además más adelante se podría incluir en un notebook un tipo de célula que sea la referencia a un algoritmos de cenit.


O convertir un algoritmo remoto de cenit a un notebook.

### 89. Datasets en Cenit. [Pacheco]

La idea es usando un modelo similar a los Object Type poder tener una interfaz de Usuario que facilite las operaciones de Datasets, en muchos casos donde los datos originales son csv, spreadsheet u otros tipos simples de datos.

Una vez cargado el spreadsheet Cenit le añade valor agregado al dataset, con el acceso al API, la interfaz de usuario con el CRUD, y las otras funcionalidades out the box con que Cenit cuenta. Por ejemplo hay veces que los usuarios quieren a partir de un spreadsheet en google crear un API, este tipo de funcionalidades sería relativamente sencilla hacerla con Cenit. 

Por ejemplo en aplicaciones de análisis de datos, es usual probar algoritmos contra Datasets que estén disponibles, en particular con la funcionalidad de Notebook, hay muchos ejemplos que se suelen hacer usando datasets.

Por ejemplo en el caso del sitio de Jupiter, ellos proporcionan esta facilidad de datasets

https://try.jupyter.org/

Crear un nuevo modelo Dataset Type que herede de Data Type.

Tener un nuevo modelo es básicamente para poder separar la lógica en la UI, de las acciones que se le puede aplicar, y que aparezca diferenciado en la navegación.


En el menú lateral tendríamos un elemento que sea Datasets, debajo de Objects y antes de Files

Al abrir el menú debe aparecer un primer link que sea Add Dataset

Este link abrirá una vista donde sea cómodo crear un nuevo Dataset, en principio, permitir cargar un csv, se asumirá que la primera fila corresponde a un header de la tabla.

Mas adelante vamos a adicionar otras opciones como cargar un spreadsheet de google drive o de otras fuentes.

Al cargar el csv se debe crear en un mismo paso el Dataset Type (idem a cómo se crea un Object Type, se asumirá que los campos todos son string) y los objects correspondiente a cada fila del CSV

Cargar y compartir los datasets que aparecen en Jupiter.

https://try.jupyter.org/

### 88. Cenit centrado en los datos.

Unas de las cosas en que Cénit tiene mayor potencial, es en la posibilidad de a partir de la creación de un Data Type  (Object Type), generar dinámicamente un grupo de funcionalidades alrededor del Data Type.


Con la creación del Data Type, tenemos hoy:

* Interfaces de Usuario (UI) que cubre un CRUD.
* Las otras funcionalidades de rails_admin, para buscar, filtrar.
* Los translator, de import y export que se pueden mejorar (incluyendo por ejemplo CSV).
* La generacion automatica de un REST API.
* Documentación del API, con el boton REST API.
* Opcionalmente la posibilidad de incluir un link en el menú de navegación. 


Qué otras cosas podemos adicionar de forma automática.

* Crear automáticamente los eventos de datos para el create_at y el update_at
* Podemos adicionar un template de webhooks, para los dos eventos create_at y update_at .
* La documentación de los webhooks se puede incluir dentro de la descripción automática del api que aparece en el botón REST * API, similar a como se hace en la especificación 3.0 de Swagger donde ellos adicionaron la especificación de webhooks.
*  Templates sencillos de notificaciones, para de forma similar a los webhooks poder notificar el cambio por diferentes vías, por ejemplo: email,  notificación interna (Cenit), u otros canales de notificación que se puedan activar por medio de una integración, como twitter, twilio
 
Al botón REST API, podemos añadirle la posibilidad de abrir un swagger spec con el visor correspondiente, mas adelante podemos agregar una spec en RAML.

Asociados a los rest API también se está trabajando en poder abrirlos con un Notebook para poder interactuar con el API e invocar los métodos.

Para demostrar mejor estas funcionalidades a un usuario nuevo, podemos crear desde el dashboard, un link ‘Add Object Type’

Ese link debe posibilitar crear un JSON Object Type, o seleccionar uno, y desde ahí poder decidir si lo visualizamos o no  en la navegación.


### 87. Adicionar las integrations a las API's de IBM Watshon. [Mary]

Los swagger specs estan disponibles en el siguiente enlacce.

[specs](https://watson-api-explorer.mybluemix.net/)

### 86. Adicionar Expedia Mobile API. [Mary]

[spec](https://www.expedia.com/static/mobile/swaggerui/)

Proponer la adicion de Guru API


### 85. Instalar cada una de las shared collections que no son de Guru APIs. [Mary]

Actualizar las integraciones propias que se han hecho que no estan en Guru API, para poder luego instalarlas en un tenant de forma independiente.


### 82. Mejorar el index de los Task y eliminar del menu a Flow executions. [Mac]

Ahora están visible los Flow executions porque tienen la ventaja que es posible ver el Flujo asociado, desde el index y así es más fácil localizar el flujo y luego las notificaciones asociadas. Pero la solución correcta sería dejar solo los Task, y en el primer campo en lugar de visualizar el tipo, que se visualice el objeto correspondiente, si es una tarea de tipo Flow Execution, se vería del mismo modo que la primera columna de Flow Execution, el tipo como tal podría ponerse en una 2da columna o no ponerse.

### 81. Mensajes internos en cenit, usando el message de MIME. [Aneli]

Ver la posibilidad de que el Mime con Message se instale por default en los tenants.

La lógica por default sería para una mensajería interna

Luego por ejemplo todas las notificaciones de error se pueden mostrar como mensajes internos

En el link siguiente aparece arriba el icon de Mails, es importante notar el dropdown que se despliega

[templete 1](http://wrapbootstrap.com/preview/WB09JXK43)

Ahí se mostrarán los mensajes más recientes, si alguien da ver más, entonces se mostrarán todos los mensajes. Ver en el template la pagina donde se muestran todos los emails

Podemos en principio usarlo para las notificaciones de error, pero luego se puede usar para otros propósitos, notificar novedades, o mensajes entre los clientes u otras funciones

en el menú podemos tener un botón (en forma de interruptor) para activar el flujo con gmail si el correo corresponde con Gmail (esto se puede extender a otros tipos de proveedores de correos, o a otras integraciones de notificación como Twilio)

### 79. Agregar Shared collection del UBL. [Mac]

En caso de Universal Business Language (UBL) esta cagada una version para el trabajo con OSSE, pero al incio de este trabajo se habia logrado cargar parcialmente la definicion original de UBL. Seria conveninete poder retomar y cargar de la manera mas completa posible UBL para publicarlo como un Shared Collection.

Diseñados para representar documentos empresariales tales como órdenes de venta o facturas. Ha sido desarrollado por un comité técnico de la organización OASIS, con la participación de varias organizaciones relacionadas con los estándares de datos en la industria. UBL está pensada para integrarse directamente en las prácticas empresariales, legales, auditoras o de gestión de registros actualmente vigentes.

### 78. Agregar Shared collection de OTA. [Mac]

Con anterioridad se lograr cargar el estándar de interoperabilidad de Viajes Open Travel Alliance(OTA), seria conveniente retomarlo y publicarlo como un shared collection.

revisar tarea: # 76

### 77. Agregar Shared Collection de X12. [Mac]

Este fue uno de los primeros estándares de EDI que se lograron cargar en Cenit, seria conveniente retomar este trabajo y publicarlo como Shared Collection.


### 76. Caso de estudio, OTA, EAN (Expedia API), Sandbox Innovation API (Amadeus). [Pacheco]

Con el propósito de aprovechar el conocimiento que tenemos en el equipo en temas de reservación de viajes, y poder contar con un nuevo caso de uso que muestre las potencialidades de Cenit

Podemos crear un esquema que permita que diferentes fuentes primarias que provean productos de viajes puedan ser transformadas al estándar de interoperabilidad Open Travel Alliance (OTA).

Inicialmente podemos probar con dos de las APIs más usadas que son además gratis, EAN de Expedia que es una API de Hoteles y con el Sandbox Innovation API de Amadeus, este último aunque tienen datos solo de prueba tiene el beneficio de contar con diferentes tipos de productos de Viaje: Flight, Hotel, Car, Rail.

Este trabajo está adelantando porque ya se ha logrado cargar OTA con anterioridad. 

Para completar este trabajo vamos a crear una web de reservación de viaje de ejemplo, en un primer momento solo con las cosas de Hoteles. Modificando las gemas de Spree Travel correspondiente y usando el template de Travelo.

Si esta prueba de concepto es satisfactoria, se pueden extender las fuentes primarias, agregando el mapeo correspondiente a OTA, mientras que lo demás debe mantenerse igual.

[OTA Introducction](https://docs.google.com/document/d/1UYXfECD7tO8scwMH6DbHfqXX7avJGij-3XSUOCVqlWY/edit?usp=sharing)

[Expedia-EAN](http://developer.ean.com/spec/)

[Amadeus Travel Innovation Sandbox](https://sandbox.amadeus.com/api-catalog)

### 73. Crear docker de cenit que pueda usar OSSE. [Pacheco]

Crear 3 contenedores Docker
Lograr que funcione local

Mongodb
Version oficial:
Imagen: https://hub.docker.com/_/mongo/
repo: https://github.com/docker-library/mongo

Version mas descarga:
Imagen: https://hub.docker.com/r/tutum/mongodb/
repo: https://github.com/tutumcloud/mongodb

RabitMQ
Version oficial
https://github.com/docker-library/rabbitmq
Imagen: https://hub.docker.com/r/_/rabbitmq/

Rails(+ Nginx, Unicorn)
repo: https://github.com/litslink/rails-nginx-unicorn

### 72. Mejoras a la implementacion preliminar de Membership. [Mac]

Una primera implementacion de Membership esta actualmente en la rama:

https://github.com/cenit-io/cenit/tree/invite_a_user

Membership es un nuevo modelo que permite la asociación many_to_many entre Users y Accounts, o sea permite gestionar los miembros (distintos al owner) de una cuenta.

Ese modelo esta decorado con Rolify, con lo cual se pueden asociar roles a los miembros, roles que van a ser especificos para ese tenant en cuestion.

Cuando se adiciona un nuevo miembro a una cuenta, se envia una invitacion por correo.

Quedan algunos puntos pendientes.

* Restringir los roles asociados a membership a: Admin, ReadOnly.

* Valorar si es viable pasar Membership para Setup y aplicarle el scope del tenant. Es importante notar que este modelo se utiliza para aceptar una invitacion con lo que ademas queda logueado el usuario.

* Revisar bien los permisos en Ability, en particular para: Account, Membership, Tenant, Role(estos ultimos para los roles usandos en membership)

* Modificar el correo, para que aparezca el nombre del modulo al que se envita

app/views/devise/mailer/invitation_instructions.html.erb

* Mejorar el disenno del correo, de modo que sea similar a otros correos que tenemos.

* Cambiar el mensaje luego de adicionar a un Membership, usar el texto de devise_invitable.en.yml

```yml
   invitations:
      send_instructions: "An invitation email has been sent to %{email}."
```

### 71. Agregar graficos de visualizacion de los modelos. [Aneli]

Agregar graficos de visualizacion de los modelos usando 

https://github.com/cenit-io/rails_admin_dynamic_charts

Es posible que sea necesario hacer cambios en la gema.

Por otra parte los graficios deben poder renderearse invocando una tarea de background, de modo que no se quede la pagina cargango.

Deberian mostrar toda las filas y no solo las correspondientes a la pagina actual.


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


### 52. Concepto de Notificación (paradigma Push/Notification). [Mac]
 
Nota: A lo que llamamos actualmente como Notifications, le debemos llamar System Notifications, de modo que este Notification es otro concepto

Con algunos cambios menores podemos acercarnos a modelar el concepto de Notificación en el paradigma Push/Notification, usado sobre todo para aplicaciones móviles, con uso también en sistemas de marketing email, y otros sistema de notificación e integración.

Por ejemplo en Marketing Email, se hacen flows para enviar correos a un Segmento específico de clientes.

En la siguiente imagen se pueden ver dos ejemplos de flujos en [Klavyio](https://www.klaviyo.com)  un sistema de Email Marketing, en el primer ejemplo se hace un flujo que envía un correo a un cliente que abandonó el un checkout, o sea un flujo asociado con un evento de cambio de estado de la orden.

[link imagen](https://drive.google.com/file/d/0B-ltzH-m3LxTbndPQzBoemNjVU0/view?usp=sharing)

Estos sistema de notificación suelen incluir el envío por SMS, Email y además de web-hooks como una opción de notificación.
Las notificaciones quedarían de forma natural dentro de la sección de Workflows

* Notifications
    * Mobile Apps
    * Email
    * SMS
    * Web-hook

Con esto podemos resolver otro problema importante, la separación del concepto de Webhooks de los conceptos de API Connection (El modelo de Webhooks actual lo vamos a deprecar, quedando solo con Operations, el nuevo web-hook, lo vamos a denotar en este documento con un guión intermedio). 

A WebHook is an HTTP callback: an HTTP POST that occurs when something happens; a simple event-notification via HTTP POST. A web application implementing WebHooks will POST a message to a URL when certain things happen.

Webhooks are "user-defined HTTP callbacks".[2] They are usually triggered by some event, such as pushing code to a repository[3] or a comment being posted to a blog.[4] When that event occurs, the source site makes an HTTP request to the URI configured for the webhook. Users can configure them to cause events on one site to invoke behaviour on another. The action taken may be anything. Common uses are to trigger builds with continuous integration systems[5] or to notify bug tracking systems.[6] Since they use HTTP, they can be integrated into web services without adding new infrastructure.[7] However, there are also ways to build a message queuing service on top of HTTP—some RESTful examples include IronMQ and RestMS.

Los tipos de notificaciones Email y SMS, deben tener un área de configuración donde se defina los proveedores de Email y SMS que se van a usar, por ejemplo GMAIL y Twilio.

* Configurations
    * ...
    * Email Config
    * SMS Config

Con los nuevos cambios que permiten definir eventos asociado a los Data Type de modelos del Setup, es posible hacer un flujo donde se envían System Notification por Email (o sea una Notificacion de tipo Email, como un caso particular de envio de email, pero para remarcar System Notification es un concepto diferente al concepto de Notificación al que se refiere este documento )

En una primera etapa podemos tener 3 tipos de notificación definidos: Web-hooks, Email, SMS. Quedando pendiente las notificaciones a Mobile Apps.

Para que el envío de notificaciones a Mobile Apps, tenga todo el sentido es necesario definir un SDK para Androi y iOS, una opción es usar (o modificar) los SDK open source de (Parse.io SDKs)[https://parseplatform.github.io/#sdks] que permitan hacer el push a Cenit de los datos.

Es importante notar que para el Push, Cenit cuenta con el API PUSH que aunque sea redundante con las opciones de POST que existe en el REST API, la API Push, puede tener la ventaja de subir en un mismo payload un Json que incluya diferentes tipos de objetos.

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

Permitir que un modo de ejecutar un flujo sea lanzarlo luego de terminada la ejecución de uno o varios flujos previos.

Este cambio debe ser suficiente para poder enlazar los flujos y definir ‘dataflows’.

Es importante notar que actualmente los Flow se puede combinar mediante eventos, pero esta alternativa podría ser una manera mas sencilla de relacionar data flows.

De modo que un flujo se podría lanzar de 3 maneras:
Mediante los triggers (data event o schedulers)
De forma manual
Definiendo flujos previos (el flujo actual se lanzaría al terminar la ejecución del flujo previo)

Estos modos de ejecución no tienen que ser exclusivos

En estos momento hay algo equivalente, mediante la definición de un callback al terminar un flujo, la diferencia básica, es que, en el flujo nuevo es donde se define los flujos previos, esto permite que cuando se termine de ejecutar un flujo ‘B’, se pueda ejecutar múltiples flujos, en caso de abajo ‘B’ y ‘C’.

- \---A 
  - \---B
  - \---C
    - \---D

A- se define como flujo previo en ‘B’ y ‘C’ 

C- se define como flujo previo en ‘D’ 

Es importante notar que ‘B’  podría ser un flujo que lo único que defina sea un traslator de tipo algoritmo, donde la salida del flujo sean datos.

Desde el punto de vista de abstracción es el nuevo flujo es el que debe tener conocimiento de los anteriores y no al revés.

Como un segundo paso podemos trabajar en un UI, que pueda lucir como esta




La ejecución por el Api de un DataFLow, devolverá un id de la tarea asíncrona, donde se pueda saber el estatus, de la ejecución del data flow completo

```Bath
cenit run DataFlow.json
```

Podria devolver algo como

```Json
{
  "runId": "2d4af716-e31d-48ef-a434-16575303752d",
  "statusURI": "https://cenit.io/run/status/2d4af716-e31d-48ef-a434-16575303752d"
}
```

```Bath
cenit run status "2d4af716-e31d-48ef-a434-16575303752d"
```

```Json
{
  "statuses": [
    {
      "jobId": "182330",
      "name": "Transformation Schema",
      "status": "Executing",
      "startTime": "May 18, 2016 11:57:26 AM",
      "endTime": "",
      "outputURI": "has no output"
    },
    {
      "jobId": "182330",
      "name": "Send Email",
      "status": "WaitCondition",
      "startTime": "",
      "endTime": "",
      "outputURI": "Job didn't run, it has no output"
    },
  ],
  "startIndex": 0,
  "itemsPerPage": 25
}
```

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


### 21. Activar el modelo de Confirmable. [Mac]

Para poder activar el modulo confirmable es necesario migrar los datos y a todos los usuarios existente asignarle a confirmed_at  Date.today-1 

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

### 2. Especializacion de Cenit en el dominio Ecommerce. [Mary]

* Basic Objects
* Sale Channels
* Integrations

Estos cambios buscan la especialización de Cenit en el dominio Ecommerce. Cenit es una plataforma genérica de integración, técnicamente las funcionalidades para Ecommerce son similares a otros dominios de aplicación, pero es importante posicionarnos en este segmento. En el menú lateral de navegación ya tenemos explícitamente los items para Ecommerce. Estos debemos moverlo dentro de un item que se llame 'Basic Objects'

* Basic Objects
  * Customers
  * Products
  * Inventory
  * Carts
  * Orders
  * Shipments
  
Aunque es posible cargar otros modelos relacionados con Ecommerce esta es nuestra biblioteca "basica", para estos modelos contaremos con funcionalidades predeterminadas en los tenants.

Las integraciones E-Commerce serán shared collections predefinidas en Cenit para servicios de Sale Channels, Shipping,  ERP, ...

Como elemento común tendrán el hecho que contengan un mapeo con modelos del namespace ECommerce de Cenit. Esto es importante para poder orquestar con facilidad varias integración de tipo ecommerce.

![ecommerce_mapping](https://user-images.githubusercontent.com/4213488/31176216-e9ecaf8a-a8c6-11e7-8501-67375b2218a3.png)

La ventaja de este enfoque es que cualquier funcionalidad que se haga a partir de los modelos del namespace Ecommerce quedaran disponibles por transitividad a otros modelos que se puedan mapear a los de Ecommerce.

Por ejemplo en las, integraciones con Sale Channels usualmente interesa enviar las órdenes que se generan a Cenit. Mientras que los servicios de entrega de paquetes (Shipping) las Órdenes salen de cenit hacia el servicio.


Veamos el siguiente ejemplo:

**Order Flow in Fancy Integration:**

- To each 20 minutes Cenit trigger a flow to get orders from Fancy Marketplace.
- When new or updated orders are received and persisted in Cenit in a Fancy Order record.
- When a created or updated Fancy Order record is saved then is trigger a Flow to transform to Order Ecommerce record in Cenit, the channel field in the record is set with the value ‘fancy’.

**Shipping Flow in Shipstation Integration**:

- When a created or updated Ecommerce Order record is saved then is trigger a Flow to transform to Shipment Shipstation record in Cenit.

- When a created or updated Shipment Shipstation record is saved then is trigger a Flow to send a shipment to Shipstation.

Las Integraciones E Commerce se deben poder adicionar tanto desde las Shared collection como desde el tab de eCommerce en el menú de navegación lateral.


**Caso de Estudio de Odoo:**

    \_ Cenit Base
           \_ Twitter connector
           \_ Gmail Connector
           \_ ….
           \_  E-commerce Connector
                       \_ Magento connector
                       \_ Prestashop Connector
                       \_ Spree Connector
                       \_ …. 


Los módulos de Facebook, Twitter y otros, pueden depender unicamente del modulo connector base (Cenit Base).
Mientras que módulos como Magento, Prestashop, Spree, etc, pueden depender de un módulo Ecommerce que extiende las funcionalidades del módulo Connector. 

Es importante notar que estos módulos de Magento, Prestashop, deben ser generados a partir de los shared collections: 

* Magento ⇔ Cenit Ecommerce
* Prestashop ⇔ Cenit Ecommerce

La regla para la generación automática sería algo asi como:

Si existe el shared collection Magento, y uno Magento ⇔ Cenit E Commerce, usar este último para la generación automática del módulo homónimo en Odoo.



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


- [rejected] ~~Cuando se salva una cross collection que tiene como pull parameter un remote cliente, dice que no lo encuentra. Por ejemplo en la cross de Magento 1.9.~~

- [rejected] ~~No se permite editar providers y remote clients despues de haberles hecho pull en un tenant.~~

- [rejected] ~~Modelos de Ecomerce no se ven en el Main Popup.~~

- [rejected] ~~Mary se logueo con la cuenta hello@omna.io, y de ahi inspeciono un nuevo tenant recien creado, desde ahi cuando  entra a los modelos de ecommerce le da un error `Model Ecommerce::Product could not be found`~~

- [rejected] ~~Pestanna "Configure" de las aplicaciones da error.~~

- [rejected] ~~No se pueden editar records de data types que tienen determinado nivel de profundidad.~~

- [rejected] ~~Objects y Security: siguen saliendo en el menu diferente a cuando se da click en Data y Gateway. Como principio, deberia siempre ser el mismo resultado si tenemos en el menu superior Cenit IO Data y Cenit IO Gateway. De modo qeu debemos valorar por ejemplo en el caso de Security, extraerlo como un nuevo subminio y mostrarlo en el menu fuera de Gateway, o mostrar el menu similar al de Gateway. En cuando Object, en ese caso no aplica lo de extraerlo fuera de data. La otra Opcion es modificar el menu superior en correspondencia a Cenit IO Objects y Cenit IO Security (Pero no me queca claro que sea la mejor opcion).~~

- [rejected] ~~si se inspecciona una cuenta y luego en el popup de menu se da click en object, sale un menu lateral diferente al de data.~~

- [rejected] ~~Cuando se da click en el link objects desde el home, sale un menu diferente al Data, no se si sea intencionalmente.~~

- [solved] ~~Al filtrar el filtro calquier dato el filtro aplicado a veces desaparece.~~

- [solved] ~~Accion de Filtrar Data types por Namespace no filtra!.~~

- [solved] ~~Accion de Filtrar flows por Namespace no filtra.~~

- [solved] ~~En vista "Collections", cualquier accion Bulk que se seleccione da error 500.~~

- [solved] ~~entre el menu lateral izq y el menu superior, debe haber una linea blanca de 1px, revisar como esta hecho en el menu lateral derecho para tratar de usar el mismo estilo css.~~

- [solved] ~~Donde dice `+ Connect Store` en `Ecommerce` valorar `+ Integration` la idea es poder instalar cualquier Shared Collection de Ecommerce, no solo los que sean Store o Marketplace. En adicion a lo anterior, cuando se da click en ese item, no deberia redireccionar al Subdominio de Integration, sino que deberia mantenerse dentro del Subdominio Ecommerce.~~

- [solved] ~~Accion de exportar un grupo de collections seleccionadas, da error 500.~~

- [solved] ~~Valorar posibilidad de agregar filtros en las notificaciones. Permitir por ejemplo filtrar por flow.~~

- [solved] ~~Cross Colleccion de Magento 2.2 da error 500 al intentar editarla.~~

### 61. Salvar los ficheros en AWS S3. [Pacheco]
 
Actualmente los ficheros que son Files Data Types, son almacenados en MongoDB.
 
Aunque es una variante rapida y sencilla para almacenar los ficheros, no es la forma mas escalable para guardar grandes volumenes de ficheros.
 
Si eliminar la opcion de almacenar en la base de datos, seria conveniente poder adicionar AWS S3 como una opcion de almacenamiento, que ademas se la opcion que configuremos para produccion en el server.

## 95. ~~Refactorizacion de la Navegacion~~.[Aneli]


- **Primaries**: Data, Compute, Gateway, Workflows
- **Domain Applications**: Integrations, APPs, Ecommerce, Marketing, Billing
- **Auxiliaries**: Monitors, Configuration, Administration

![new_home](https://user-images.githubusercontent.com/4213488/28572386-de5a455e-7114-11e7-909e-de9e22cf92bf.png)

![data](https://user-images.githubusercontent.com/4213488/28572427-043dca84-7115-11e7-9410-5cba5db00631.png)

================= PRIMARIES===================

#### DATA

- **Definitions** 
	* Data Types
		+ Object Types
		+ File Types
	* Validators
		+ Schemas
		+ EDI Validators
		+ XSLT
		+ Algorithm Validators
- **Objects**
	* Add Object Type + 
- **Files**
	* Add File Type + 


#### WORKFLOWS

- **Flows**
- **Triggers**
	* Data Events 
	* Schedulers
- **Notifications**
	* Mobile Apps
	* Email
	* SMS
	* Web-hook
- **Channels**
- **Transformations** 
	* Render (type exporter)
		+ HTML (html.erb, liquid)
		+ JSON (json.rabl)
		+ XML (xml.rabl, xslt)
		+ JS (js.erb)
		+ PDF (pdf.prawn)
		+ CSV (csv.erb)
		+ Text (txt.erb)
	* Parser (type importer)
	* Convert
	* Updater

#### GATEWAY

- **Connectors**
	* API Connections
	* Resources
	* Operations
	* Connection Roles  (eliminar de la navegación)
- **API Spec**
	* Add API Spec + (Action)
	* OpenAPI Directory
- **Security**
	* Clients
		+ OAuth
		+ AWS
	* Providers
		+ OAuth 1.0
		+ OAuth 2.0
	* Scopes
		+ OAuth 2.0
		+ OAuth Grant Access 
	* Authorizations
		+ Basic
		+ Digest
		+ OAuth 1.0
		+ OAuth 2.0


#### COMPUTE

- **Snippets**
- **Algorithms**
- **Cloud functions** (estos son los algoritmos remotos que hizo pacheco)
- **Serverless**
- **Background Jobs**


================= DOMAIN APPLICATIONS===================

#### INTEGRATIONS

- **My Collections**
- **Shared Collections**

#### APPs

#### ECOMMERCE

- **eCommerce**
	* Customers
	* Products
	* Orders
	* Payments
	* Shipments
- **Sale Channels**
	* Connect Store +
	* Fancy
	* Mangeto
	* Custom Store

- **Integrations**
	* Odoo
	* Shipstation


#### MARKETING

- **Customers**
- **Leads**
- **Email Automation**
- **Social Posting**



================= AUXILIARIES===================


- **Monitors**
	* System Notifications
	* Running Jobs (rename Tasks)
	* Storages
- **Configurations**
	* Namespaces
	* Connection Configs
	* Data Type Configs
	* Flow Configs
	* Email Config
	* SMS Config
	* Pings
	* Bindings
	* Parameters
- **Administration**
	* Users
	* Accounts
	* Roles
	* Application IDs
	* Scripts
	* Script executions
	* Rabbit Consumers
	* Delayed Messages
	* Shared Names
	* System notifications
	* Tokens



### 54. ~~Migrar a rails_admin 1.0~~. [Aneli]

Rails Admin hizo el release de la version 1.0, por lo que es un buen momento para hacer un upgrade de Cenit. Es importante revisar todas las vistas que tenemos customizadas en Cenit.


### 30. ~~Crear el Shared Collection de Cenit a partir del spec en el directorio de Guru API~~. [Mary]

Actualizar el script que lee las especificaciones del directorio de Guru API que ya incluyen el spec de Swagger de Cenit IO y generar el Shared Collection de Cenit, con la misma logica que se genera cualquier otro spec.

### 56. ~~Crear Shared Collection de Spree.~~ [Mary]

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


### 64. ~~Usar el mismo estilo de codigo en Show que en los Edit~~. [Aneli]

Esta tarea esta bastante adelantada. Solo completar el trabajo con otros modelos a los que se le puede aplicar. Schemas, Json Data Type, a los diferentes tipos de transformations. 

La propuesta es poder utilizar el mismo estilo de codemirror para el codigo en las vistas Show que en las vistas Edit, con la diferencia de que el codigo en los Show no puede ser Editable.


### 69. ~~Mejoras a la acccion REST API~~. [Pacheco]

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


### 9. ~~Cambiar el nombre del modelo Account por Tennant~~. [Mac].

Ahora en Cenit es posible tener asociado a un usario varias "Accounts" con lo cual es mejor renombrar el concepto de "Account" por "Tennant" 
 
### 5. ~~El email y el pdf de OSSE no soporta tildes~~. [Mac]
 
Al parecer porque es UTF-8, hay que revisar la posibilidad de seleccionar el enconde




### 24. ~~API Connection ⇔  Swagger Spec~~. [Pacheco]

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

### 23. ~~Adicionar en el menú superior indicador para storages~~. [Aneli]

Cuando se esta logueado se muestran los monitors en ese grupo esta pendiente por adicionar a los storage.


### 75. ~~Diferenciar visualmente los shared cross del resto de los objectos~~. [Mac]

Visualmente debemos hacer mas evidente a los usarios la diferencia entre lo que es shared cross y lo que no, de manera que se confunda lo menos posible. 

Una primera accion puedes ser

Mostrar el icon de la cantidad en verde de forma que permita diferenciar visualmente los objetos compartidos del resto de los objetos que se muestran con la cantidad en azul.

Pensar en otros recursos que ayuden a esta diferenciacion

### 83. ~~Mostrar el index de los modelos de Ecommerce sin necesidad de loguearse~~. [Mac]

En caso de los Objetos de Ecommerce, sería conveniente que se pueda mostrar el index, sin necesidad de loguearse, de ese modo se pueden ver los campo y además puede aparecer el link al API. El index sai no se esta logueado debe aparecer vacio.


### 80. ~~Cenit Notebooks~~. [Pacheco]

Cenit Notebooks

En varios momentos durante el proyecto hemos pensado cómo tener una manera de poder describir instrucciones en cenit, que a la vez sean posibles ejecutar.

De hecho algunas cosas se lograron (por Mac) en ese sentido, como los readme de las shared collections o los post que se publicaron de Cenit.

También lo analizamos en la competencia como en el caso de Mulesoft, donde en sus Notebooks pueden especificar ejemplos de cómo interactuar con las APIs.

Esta funcionalidad la podemos usar como parte de una documentación mas orgánica dentro del propio cenit, donde se puede explicar como funciona cenit, teniendo además elementos que sean posibles ejecutar. Que es una de las piezas que no ha estado faltando, cómo lograr que la documentación sea un contenido propio de cenit y no un elemento aislado. 

Hay un proyecto open source Jupyter Notebook que inicialmente fue desarrollado por la comunidad de python, y que ha tenido mucha aceptación por parte de la comunidad, que es justamente un notebook, actualmente se ha extendido a  varios lenguajes.

“The Jupyter Notebook is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text. Uses include: data cleaning and transformation, numerical simulation, statistical modeling, machine learning and much more.”




### 84. ~~Adicionar el Sandbox API Innovation de Amadeus~~. [Mary]

El Swagger esta disponible en esta URL

[spec](https://github.com/amadeus-travel-innovation-sandbox/sandbox-content/blob/master/swagger.yml)


### 73. ~~Hacer los modelos Shared visibles sin autenticacion para el index y el show~~. [Mac]

Para los objetos que son compartidos (cross shared) deberian ser visibles las acciones de index y show sin necesidad de autenticarse.

Esto debería aplicarse igual para el API.

### 74. ~~Ejecucion de remota de los algoritmos de Cenit~~. [Mac]

Con la gema cenit-algorithms que se encuentra en github en:

https://github.com/cenit-io/cenit-algorithms

es posible ejecutar de forma remota algoritmos en Cenit.

Tan sencillo como:

```Batch
$ gem install cenit-algorithms

$ irb
> require 'cenit/algorithms'

> Cenit::Algorithms('Number Theory').factorial(5)  # 120

> Cenit::Algorithms('Number Theory').gcd(20, 15)   # 5
```

Los algoritmos disponibles se pueden ver en:

https://cenit.io/algorithm

Si se desea agregar la posibilidad de ejecutar algoritmos en un proyecto en Rails, se debe incluir la gema en el Gemfile

	gem 'cenit-algorithms'
	
Que viene mas adelante:

* La posibilidad de que se puede ejecutar los algoritmos desde los SDK, para que pueda ser posible correrlo desde otros lenguajes.

* Los algoritmos en Cenit actualmente son en Ruby, se esta trabajando en extender esta posibilidad a otros lenguajes.

* Si la ejecucion del algortimo tarda mucho, se deberia retonar una tarea, en la cual se pueda ir chequeando el status.

* Hay que revisar como esto puede impactar los planes de precio de Cenit.

### 70. ~~Implementar una ventana flotante de contact us~~. [Aneli]

esta rama tiene la logica adelantada pero no esta funcionando.

https://github.com/cenit-io/cenit/tree/add_contact_us

### 20. ~~Mejorar y expandir el uso de los tags.~~ [Aneli]

Los tags fueron adicionados por Daniel para los Algoritmos. Pero usan la interfaz por default de rails_admin para las relaciones Many to Many con dos text area uno al lado del otro, donde es posible seleccionar los tag y pasarlo a la otra area..

1. Mejorar la interfaz de los tags, para que sea un imput de múltiples tag con autocompletamiento. Revisar las librerias de JQuery existentes.

2. Adicionar los tags a otros modelos como las Collecciones y los Shared Collections, revisar que otros modelos se pueden beneficiar de esto, pero la intencion es que sea un patron que podamos relacionar con todos los modelos que necesitan funcionalidades que faciliten el *discovery*.


### 62. ~~Completar las categorias y tags de las Shared Collections.~~ [Aneli, Mac]

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

### 63. ~~Lanzar el Tour automáticamente~~. [Aneli]

Que el tour se lance automaticamente, la primera vez que alguien se loguea, o se conecta desde un IP.

### 66. ~~Adicionar un Save Filter~~. [Aneli]

El modelo Query fue renombrado como Filter, por varias razones:

1- Para usar el mismo nombre que usa rails_admin, al final es persistir los filtros actuales que ellos tienen en las vistas

2- Para reservar el termino Query, al nuevo API [GraphQL](http://graphql.org/)

Con este nuevo nombre es mas intuitivo poder hacer la funcionalidad de salvar un filtro dinamico cuando se adicione a una vista cualquiera. O sea esta seria una forma alternativa a la forma actual (que es el al modelo Filter y crear un nuevo filter). En las vistas de rails_admin por default viene un Add Filter, una vez selecionado Add Filter apareceria un boton asociado 'Save' para poder persistir el filtro.

### 68. ~~Vistas de index embebidas deben mostrar las acciones con los 3 puntos verticales~~. [Aneli]

En las vistas de index embebidas como la que se usa en el show de los cross_shared_collections, las acciones asociada a cada fila, se deben mostrar con los 3 puntos verticales, de modo que sea uniforme con el resto de la plataforma.

En caso de la accion Filters, revisar como se puede convertir en una vista embebida, e igualmente mostrar las acciones.


### 65. ~~En 'send to flow', mostrar la tabla o la cantidad de elementos a los que aplica~~.  [Aneli]

En la accion send to flow es conveniente que se mueste debajo la tabla de los elementos a los que va a aplicarse la accion.

En caso qeu la tabla no sea lo mejor, mostrar la cantidad de elementos.

Esto es para evitar que una accion de flow se aplique a elementos que no se desea. 

Pensar ademas como mejorar el siguiente escenario.

Cuando usuario marca algunas filas y luego va directamente a 'send to flow' en lugar de tomar las filas marcadas, se toman todas las filas, ya no se uso la accion 'Selected Items', seria bueno mejorar la experiencia de usuario en este caso, quizas mostrando un warning, o seleccionando los elementos marcado que una opcion para seleccionar todos si era la intencion.

### 53. ~~Modelos para soportar API SPec sincronizacion con Sagger~~. [Mac]

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

En el listado de acciones, que han

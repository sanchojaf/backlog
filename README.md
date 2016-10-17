# backlog

### 35. Cenit local no esta salvando correctamente los objetos. [Mac]

En mi instancia local de Cenit, cuando creo los namespace no aparecen luego en el listado del index

Lo mismo me paso creando un JSON Data Type, cuando doy save aparentemente salva satisfactoriamente, pero luego el listado aparece vacio.

Cree una cuenta nueva y paso lo mismo, previendo que mi cuenta estuviese corrupta.

### 34. Errores en los algoritmo en produccion. [Mac]

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


### 32. Actualizar la pagina actual de la documentacion del API. [Mary] 

Actualizar la documentacion del API, en correspondencia con el Swagger.

La URL de documentacion del API es:

- http://cenit-io.github.io/docs/api/

La URL del Swagger es:

- https://cenit.io/openapi/v1/swagger.json

Para actualizar la pagina de documentacion se debe modificar dos ficheros JS:

- https://github.com/cenit-io/docs/blob/gh-pages/api/api_project.js
- https://github.com/cenit-io/docs/blob/gh-pages/api/api_data.js

Esta actualizacion debe ser temporal porque debemos lograr que la pagina de documentacion del API se genere automaticamente a partir del fichero Swagger.

### 31. Crear tarea que genere el swagger.json a partir del swagger.yml [Mary]

La generacion del swagger.json debe ser programatica'de modo que cada vez que se modifique el swagger.yml sea posible correr un rake task como

    rake openapi:ymltojson

Que lea el yaml:

    /public/openapi/v1/swagger.yaml

y sobre escriba el json:

    /public/openapi/v1/swagger.json
    
### 30. Crear el Shared Collection de Cenit a partir de Guru API. [Mary]

Actualizar el script que lee las especificaciones en Guru API que ya incluyen el spec de Swagger de Cenit IO y generar el Shared Collection de Cenit como otro cualquiera.

### 29. Probar y actualizar las integracion de Cenit con Odoo 9. [Mary]

Intalar Odoo 9 y probar cada una de las ingegraciones con Odoo 9.

Como parte de la actualizacion revisar la documentacion.

### 28. Crear una integracion de Magento basada en el Swagger. [Mary]

Encontramos el Swagger de Magento y fue annadido a Guru API, de modo que debemos actualizar la sincronizazcion de las shard collections para poder contar con esta integracion de Magento y posteriormente agregarla a las Integraciones disponibles para Odoo.

### 27. Crear Integracion para Spree Ecommerce. [Mary]

Es importante trabajar en esta integracion con Spree. Es una tegnologia que dominamos y podemos tener potenciales clientes. Hay muchas pruebas que podemos realizar con Spree, similares a las que realizamos para Odoo.

### 26. Permitir importar diferentes tipos de API Spec. [Mac] 

Esta tarea esta inciada por parte de Mary, se 
(Swagger, RAML, I/O Docs, Google Discovery, WADL, API, API Blueprint)

### 25. Usando el API de Cenit generar los modulos de integracion de Odoo. [Pacheco]

Actualmente en Cenit tenemos unas 276 integraciones, de estas integraciones unas 10 las hemos adecuado a modulos de integracion Cenit Odoo, lo cual permite a Odoo integrarse con terceros sistemas a traves de Cenit.

La mayoria de los clientes que han llegado a Cenit han sido a partir de conocer estas integraciones en Odoo.

En esta URL se pueden ver los modulos publicados en Odoo apps

- https://www.odoo.com/apps/modules/browse?search=cenit

Daniel incio un proyecto en python que de forma programatica permite generar un addons de Odoo correspondiente a la integracion por un shared collection en Cenit.

- https://github.com/cenit-io/odoo-cenit-collection-bundler

Esta generacion automatica se puede hacer a partir de la informacion de un Shared Collection que se obtiene a traves del API. El proyecto no se ha actualizado en mas de un anno, durante ese tiempo se ha modificado el API.

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
    

### 24. API Connection ⇔  Swagger Spec [Pacheco]


La Ideas es que un Swagger Spec se pueda hacer corresponder con un API Connection y sus conceptos relacionados de Resources y Webhooks

Revisar la siguiente presentacion para tener mas elementos relacionados con esta tarea

https://docs.google.com/presentation/d/1U7npFSNCPMDZDrDZyPNuP9blxEZmcxFGkDDvTFm2nqw/edit?usp=sharing


* API Connections 
  * Resources
    * Webhooks

Lo que es lo mismo que:
* Webhooks belogs_to Resource
* Resource belogs_to API Connection 

nota: el nombre de webhooks no es el mas apropiado, pero de momento seguiremos usando se puede enteder como Metodo o Operacion, y incluye la especificaicon del Metodo HTTP y ademas de los parametros.


En lo posible vamos a tratar de tener resultado parciales que podamos desplegar.

1. Tener una nueva accion que sea Swagger que permita abrir como read only la conversion a swagger del API Connection

2. Mas adelante debemos poder editar el Swagger y su edicion debe modificar la configuracion de API Connection, o sea existir una sincronizacion entre los modelos en la base de datos y el fichero Swagger.

3. Agregar una vista del swagger similar a la de Swagger Editor, una variante es ver si es posible embeber el Swagger Editor en Cenit 

### 23. Adicionar en el menú superior indicador para storages. [Aneli]

Cuando se esta logueado se muestran los monitors en ese grupo esta pendiente por adicionar a los storage.

### 22. Limitar el listado de acciones a 4 y luego un boton que diga more. [Aneli]

Un boton more, inmediatamente a la derecha de las primeras 4 acciones. 
Este boton debe permitir desplegar el resto de las acciones.

(Opcional) al lado del boton se puede mostrar entre parentisis la cantidad de accciones adicionales que hay.

### 21. Activar el modelo de Confirmable. [Mac]

Para poder activar el modulo confirmable es necesario migrar los datos y a todos los usuarios existente asignarle a confirmed_at  Date.today-1 

### 20. Mejorar y expandir el uso de los tags. [Aneli]

Los tags fueron adicionados por Daniel para los Algoritmos. Pero usan la interfaz por default de rails_admin para las relaciones Many to Many.

1. Mejorar la interfaz de los tags, para que sea un imput de múltiples tag con autocompletamiento. Existen librerias Jquery para esto.

2. Adicionar los tags a otros modelos como las Collecciones y los Shared Collections, revisar que otros modelos se pueden beneficiar de esto.

### 19. Mejorar el tour. [Aneli]

Del tour se hizo una primera implementacion en el portal anterior de Cenit por parte de Daniel, se puede ver aqui

- https://cenit-portal.herokuapp.com/

Y en repo

- https://github.com/cenit-io/cenit-portal

Hacerlo abriendo los elementos hojas del sidebar lateral de navegación, ir abriendo los niveles y cerrando en la medida que el tour avanza.

### 18. Cambiar  los has_many en los index mostrando la cantidad. [Aneli]

Cambiar la vista por default de index de rails_admin, para que las columnas que se corresponden con una relación has_many mostrando los 3 primeros elementos de la lista y luego un número con la cantidad total de elementos

### 17. Incluir un link a los webhooks en show de los shared collections. [Aneli]

Cuando un shared collection tiene muchos webhooks, desde el show no es posible revisarlos todos. Por ejemplo en caso de Gmail, solo se muestran 35 de un total de 56. Sería conveniente un link que al darle click redireccione a la pagina de los webhooks y estos aparezcan filtrados, mostrando solo los que pertenecen al Flow.

### 16. Adicionar estadisticas de los monitors en el dashboard. [Mac]

En el dashboad se muestran 3 regtangulos con los monitors:

* running task
* autorizactions
* notifications

Cada uno debe mostrar la cantidad correspondiente

### 15. Push asincronos. [Mac]

Un push a Cenit mediante el API debe ser procesado de forma asíncrona, en el momento del push se debe retornar el ID de una Tarea, de modo que posteriormente se pueda indagar por el estado de la ejecución de la tarea.
Por ejemplo la tarea que se devuelva asociada a un push, puede estar relacionada con otras tareas.

Una tarea puede generar otras subtareas y se necesita recuperar ese arbol de dependencias para poder saber si todo se termino correctamente

### 14. Permitir múltiples usuarios por cuenta. [Mac]

Ya esta implementado Multiples cuentas por usuario.

Permitir múltiples usuarios por cuenta,  se debe tener al menos dos roles dentro de account, el role de  owner de la cuenta y  una con otro Rol (que en el futuro limite por ejemplo la vista de factura, o de adicionar usuarios y cambiar los roles dentro del tenant, etc)

El rol Owner tendria acceso en  el dashboard al area de administración

### 13. Crear una nueva cuenta con dos tenants predefinidos TEST y LIVE. [Mac]

Test, Live

Los ultimos cambios en Cenit permiten que asociado a un usuario podamos tener varios Tenants 

Estos tenant son espacios de trabajo independientes que se pueden utilizar con diferentes fines:

En el caso de OSSE los tenants corresponden a sus empresas clientes, cada tenant tendra los documento de factura electronica correspondiente a una empresa.

Otros lo pueden usar como un ambiente de trabajo, ejemplo: Test, Live

Para promover esta funcionalidad en Cenit conviene que cuando se lance una nueva cuenta en Cenit, esten predeterminado dos tenants, correspondientes a los ambientes: Test y Live. Siendo Live el ambiente predeterminado. 

Dando la opcion adicional que se pueda crear un tenant nuevo.

### 12. Usar las url con slug como url por default en lugar del ID. [Mac]

Ya en Cenit se soportan las url con slug y ademas de las id, en adicion seria conveniente que las url predeterminadas en la documentacion sean con slug. Esto ademas ayudaria a que sean indexadas por los motores de busqueda.

### 11. Eliminar ‘setup~’ prefijo de las url. [Mac]

Todas las url tienen el prefijo 'setup~' que lo toma rails_admin de la carpeta setup. eliminar este prefijo que no cumple funcion.

### 10. Redireccionar los link de notificaciones a filtros. [Aneli]

En el menu superior aparece un icon de las notificaciones y asociado con el icon diferentes numeros relacionados con el tipo de notificacion, cuando se le da click a uno de los numeros esta redireccionando a las notificaciones, pero no a las notificaciones filtradas por el tipo de notificacion del numero.

### 9. Cambiar el nombre del modelo Account por Tennant. [Mac].

Ahora en Cenit es posible tener asociado a un usario varias "Accounts" con lo cual es mejor renombrar el concepto de "Account" por "Tennant"

### 8. Definir un Segmento en los Datos asociado a un Data Event. [Mac]

Por ejemplo si se define un evento de Placed Order para las ordenes con status Placed
Que automáticamente en la navegacion del menu lateral se cree un subnivel para Placed Orders

Donde podamos inspeccionar este subconjunto de las ordenes, y tenga solamente los flujos asociados con ellas (en caso que existan flujos definidos)

Una misma orden puede estar en varios segmentos.

### 7. Los Récords por default deben ser visibles en la navegación. [Mac]

I)
Aun cuando hay casos como X12 que tienen cientos de de modelos, la mayoría de los shared collections que tenemos tiene pocos modelos.

El sidebar tiene hoy implementado un scroll que hace que no sea tan engorroso la navegación, además tendremos la opción de poderlos eliminar del menú si se desea. Incluso podemos agregar un acción sobre la lista, por ejemplo si se instala X12 se podría tener una opción en el collection (o en otro lugar mas visible) que permita eliminar todos los modelos de la navegación de records,

II)  La otra parte de la propuesta es en lugar de tener Records en la navegación sustituirlo por dos conceptos Objects y Files, correspondiendo a JSON Data Types y File Data Types.

III) Cuando no se este logueado que en el menú lateral aparezca Objects y Files pero que no se puedan expandir.

### 6. Mejorar navegación e interfaz de las Transformaciones. [Aneli, Mac]

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
 
 
### 5. El email y el pdf de OSSE no soporta tildes. [Mac]
 
 Al parecer porque es UTF-8, hay que revisar la posibilidad de seleccionar el enconde
 
 
### 4. Generar los SDK para ruby, python, node.js. [Pacheco]
 
 Generar los SDK correspondientes al API de Cenit para los principales leguajes de programacion

### 3. Subdominios para las aplicaciones. [Pacheco]

Para que las aplicaciones tegan mayor valor de uso, es importante que se pueeda asociar un dominio o subdominio propios.

- www.userdomain.com
- www.sub.userdomain.com

Para esto debemos desplegar las aplicaciones en un sudominio de cenit.io, preferentemente generado alearotiamente, de modo que no tengamos colisiones con los subdominios que deben ser reservados a cenit. Ejemplo

- https://polar-wave-7672.cenit.io

Para esto tenemos que asociar un certificado wildcard con el dominio cenit.io

Hay que ver como es posible configurar Nginx para que dinamicamicamente pueda responder a estos dominios o subdominios propios

Por ejemplo para una web como mytriptomoon, podria tener una aplicacion para la autenticacion con varios provedores de identidad usando cenit, que desee que se visualice en:

https://signin.mytriptomoon.com

### 2. Agregar a la navegacion Ecommerce. [Mac]

Las motivaciones de este cambio son para hacer mas evidente las posibilidades que tiene Cenit para el mundo Ecommerce. Cenit es una plataforma genérica de integración, y técnicamente las funcionalidades para el tema ecommerce son similares a otros dominios de aplicación, pero es importante diferenciar ese segmento. Similar a Google Analitic, que permiten monitorear la actividad en el sitio web, definiendo eventos customizados de acciones específicas en la web que se desean monitorear, mas allá de la funcionalidad genérica tiene una seccion especifica para Ecommerce.

Propongo que en el menu de navegacion tengamos explicitamente un item para Ecommerce, y como segundo nivel tendriamos: Customers, Products, Orders, Shipments, Payments. Los modelos de ese namespace estarian pre-instalados en cada nuevo tenant que se lance.

* Ecommerce
  * Customers
  * Products
  * Orders
  * Payments
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


### 1. Algoritmos remotos. [Pacheco]

Cenit Algorithms

En Cenit podemos pensar en dos tipos de algoritmos, local or remote, 

Los algoritmos locales: son los que tenemos actualmente, tiene full acceso a la bd de cenit, de momento solo soportados en ruby, y no permiten referencias a bibliotecas. Deben poderse ejecutar de forma sincrona o asincrona

Algoritmos remotos: la comunicación con cenit sería mediante el api, y debe ser programada, soportados múltiples lenguajes mediante la tecnología del buildpacks,  permiten incluir referencias a bibliotecas. Deben ser siempre ejecutados de forma asíncrona.

Cada ejecución del algoritmo es representada por una tarea asíncrona en Cenit.

De forma opcional el output es definido por un DataType. Cada ejecución del algoritmo puede tener un set de objetos del data type (con cenit, pueden ser exportados como JSON, XML, CSV, etc)


Algoritmos remotos

Un algoritmo por default no tendría nada para la comunicación con los modelos de Cenit. Pero para lograr esto podemos en el template (un gist) agregar una secuencia de pasos comentados, que permitan leer los parametros del algoritmo desde cenit, mediante un push (HTTP Post) retornar el resultado del algoritmo a cenit.

Del mismo modo puede estar comentadas otras operaciones con el API de cenit. En caso que se desee leer objetos del setup(conectores, tareas etc)

Por ejemplo el template para ruby, tendría el Gemfile, Gemfile.lock y un algorithm.rb, un template similar al que crea morph.io, por ejemplo:
https://github.com/sanchojaf/city_test3/blob/master/scraper.rb

Como el algoritmo puede ser público es importante que las credenciales se suban al buildpack como variables de ambiente.


Input

curl GET -H "X-User-Access-Key: N63563526" -H "X-User-Access-Token: TYQTWY454521QQ12" \
https://www.cenit.io/api/v1/algo/#namespace/#algo_name/input

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

Modificar los parametros de entrada y la salida de los algoritmos

Por cada parámetro de entrada, debemos:
Eliminar la descripcion del parámetro (el algoritmo tiene una descripcion donde se puede describir los parametros), ademas el nombre debe ser suficiente para que se entienda de qué es el parámetro.
Especificar si el parámetro corresponde a una lista o un solo elemento, por default asumir que es un solo elemento
Poder asociar de forma opcional un Validator. El Validator puede ser un schema o cualquier otro tipo de validador.
Permitir definir un valor por default del parámetro. 
Especificar si el parámetro es obligatorio u opcional (por default obligatorio). 

El algoritmo debe tener un área que sea Sample, donde se pueda asociar un conjunto de valores correspondiente a cada uno de los  parametros de entrada. 

En la pestaña Run en lugar de tener un textarea para el imput, se debe cargar un field imput por cada parámetro de entrada con el label que sea el name del parámetro, debe poder cargar el valor por default en caso que esté’ definido, si el parámetro es una lista, se deben poder entrar los valores de entrada separado por signo de coma.

Si el algoritmo tiene un sample definido, En el Run debe aparecer un checkbox que sea ‘load sample’ por default en false. Si se marca en true todos los parametros de entrada  toman los valores correspondientes definidos en el sample..

Debe existir un tiempo maximo de ejecucion para el algoritmo síncrono, y un tiempo máximo para el asíncrono (en este último se debe permitir un tiempo mayor de ejecución). Esa información de los tiempos máximos debe aparecer como una info en el Run,

(La funcionalidad a continuación podemos dejarla para más adelante)
En relación con la salida de los algoritmos, cuando se seleccione validar la salida, se debe poder seleccionar varios Validators, los validators pueden ser un schema o cualquier otro validator, si está seleccionado un Data Type de salida, y se marca validar se puede cargar ese mismo esquema como un primer validator, pero el usuario puede eliminarlo si lo desea.

Agregar un nuevo action para mostrar el output de la última ejecución visualmente similar a la página a la que se llega cuando se le da click al icon de records de el  output más reciente que se muestra en show. La idea es que la última ejecución este’ más jerarquizada que el resto de las ejecución y que sea sencillo inspeccionarla, exportar los datos, etc


Sobre el el modelo Algorithm Output:
Almacenar el valor de los parametros de entrada.
Hay que buscar la manera de poder salvar el inicio de la ejecución y la duración.

Hay una herramienta q es una variante open source ligera de heroku, se llama dokku. Heroku hizo open source los buldpacks, la mayoria de las plataforma de computo azure, google cloud. Permite desplegar una app a partir del buildpack. En cenit queremos correr buildpaks en diferentes lengiajes. Eso seria prinero para los algoritmos en cenit. Scripts con referencias a bibliotecas, ruby, python, node.js pero tambien para un concepto de aplicaciones q tenemos en cenit, hoy son aplicaciones sinatras pero podrian ser un aplicacion web definida por buildpack

Dokku tiene un deamon. Seria trabar en un api para dokku. Donde se pueda hacer un despliegue de una app programatixamente


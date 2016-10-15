# backlog

### Cenit local no esta salvando correctamente los objetos. [Mac]

En mi instancia local de Cenit, cuando creo los namespace no aparecen luego en el listado del index

Lo mismo me paso creando un JSON Data Type, cuando doy save aparentemente salva satisfactoriamente, pero luego el listado aparece vacio.

Cree una cuenta nueva y paso lo mismo, previendo que mi cuenta estuviese corrupta.

### Errores en los algoritmo en produccion. [Mac]

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

### Actualizar la pagina actual de la documentacion del API. [Mary] 

Actualizar la documentacion del API, en correspondencia con el Swagger.

La URL de documentacion del API es:

- http://cenit-io.github.io/docs/api/

La URL del Swagger es:

- https://cenit.io/openapi/v1/swagger.json

Para actualizar la pagina de documentacion se debe modificar dos ficheros JS:

- https://github.com/cenit-io/docs/blob/gh-pages/api/api_project.js
- https://github.com/cenit-io/docs/blob/gh-pages/api/api_data.js

Esta actualizacion debe ser temporal porque debemos lograr que la pagina de documentacion del API se genere automaticamente a partir del fichero Swagger.

### Crear tarea que genere el swagger.json a partir del swagger.yml [Mary]

La generacion del swagger.json debe ser programatica'de modo que cada vez que se modifique el swagger.yml sea posible correr un rake task como

    rake openapi:ymltojson

Que lea el yaml:

    /public/openapi/v1/swagger.yaml

y sobre escriba el json:

    /public/openapi/v1/swagger.json
    
### Crear el Shared Collection de Cenit a partir de Guru API. [Mary]

Actualizar el script que lee las especificaciones en Guru API que ya incluyen el spec de Swagger de Cenit IO y generar el Shared Collection de Cenit como otro cualquiera.

### Probar y actualizar las integracion de Cenit con Odoo 9. [Mary]

Intalar Odoo 9 y probar cada una de las ingegraciones con Odoo 9.

Como parte de la actualizacion revisar la documentacion.

### Usando el API de Cenit generar los modulos de ingracion de Odoo. [Pacheco]

Actualmente en Cenit tenemos unas 276 integraciones, de estas integraciones unas 10 las hemos adecuado a modulos de integracion Cenit Odoo, lo cual permite a Odoo integrarse con terceros sistemas a traves de Cenit.

La mayoria de los clientes que han llegado a Cenit han sido a partir de conocer estas integraciones en Odoo.

En esta URL se pueden ver los modulos publicado Odoo apps

- https://www.odoo.com/apps/modules/browse?search=cenit

De modo que seria bueno tener una manera programatica que nos permita generar de forma automatica el modulo correspondiente de integracion en Odoo para cada una de las shared collection que tenemos.

Esta generacion automatica se puede hacer a partir de la informacion de un Shared Collection que se obtiene a traves del API.

Un proyecto similar hicimos hace un tiempo, con gema cenit_cmd, una gema que generaba el directorio de nuevas gemas en ruby a partir de un shared collections al final lo qeu se genera es una coleccion de ficheros y carpetas.

Del mismo modo podemos crear una gema ruby que lea el API de cenit y genere el directorio corrrespondiente a una integracion en Odoo o annadir esta logica dentro de la misma gema cenit_cmd

https://github.com/cenit-io/cenit_cmd


En este repo estan los modulos actuales de las integraciones en Odoo.

- https://github.com/cenit-io/odoo-integrations

Por ejemplo, la integracion particular de Twilio, se puede encontrar en

- https://github.com/cenit-io/odoo-integrations/tree/8.0/cenit_twilio

y es un subdirectorio con la siguiente estructura

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
  

### Adicionar en el menú superior indicador para storages. [Aneli]

Cuando se esta logueado se muestran los monitors en ese grupo esta pendiente por adicionar a los storage.

### Limitar el listado de acciones a 4 y luego un boton que diga more. [Aneli]

Un boton more, inmediatamente a la derecha de las primeras 4 acciones. 
Este boton debe permitir desplegar el resto de las acciones.

(Opcional) al lado del boton se puede mostrar entre parentisis la cantidad de accciones adicionales que hay.

### Mejorar y expandir el uso de los tags. [Aneli]

Los tags fueron adicionados por Daniel para los Algoritmos. Pero usan la interfaz por default de rails_admin para las relaciones Many to Many.

1. Mejorar la interfaz de los tags, para que sea un imput de múltiples tag con autocompletamiento. Existen librerias Jquery para esto.

2. Adicionar los tags a otros modelos como las Collecciones y los Shared Collections, revisar que otros modelos se pueden beneficiar de esto.

### Mejorar el tour. [Aneli]

Del tour se hizo una primera implementacion en el portal anterior de Cenit por parte de Daniel, se puede ver aqui

- https://cenit-portal.herokuapp.com/

Y en repo

- https://github.com/cenit-io/cenit-portal

Hacerlo abriendo los elementos hojas del sidebar lateral de navegación, ir abriendo los niveles y cerrando en la medida que el tour avanza.

### Cambiar  los has_many en los index mostrando la cantidad. [Aneli]

Cambiar la vista por default de index de rails_admin, para que las columnas que se corresponden con una relación has_many mostrando los 3 primeros elementos de la lista y luego un número con la cantidad total de elementos

### Incluir un link a los webhooks en show de los shared collections. [Aneli]

Cuando un shared collection tiene muchos webhooks, desde el show no es posible revisarlos todos. Por ejemplo en caso de Gmail, solo se muestran 35 de un total de 56. Sería conveniente un link que al darle click redireccione a la pagina de los webhooks y estos aparezcan filtrados, mostrando solo los que pertenecen al Flow.

### Adicionar estadisticas de los monitors en el dashboard. [Mac]

En el dashboad se muestran 3 regtangulos con los monitors:

* running task
* autorizactions
* notifications

Cada uno debe mostrar la cantidad correspondiente

### Push asincronos. [Mac]

Un push a Cenit mediante el API debe ser procesado de forma asíncrona, en el momento del push se debe retornar el ID de una Tarea, de modo que posteriormente se pueda indagar por el estado de la ejecución de la tarea.
Por ejemplo la tarea que se devuelva asociada a un push, puede estar relacionada con otras tareas.

Una tarea puede generar otras subtareas y se necesita recuperar ese arbol de dependencias para poder saber si todo se termino correctamente

### Permitir múltiples usuarios por cuenta. [Mac]

Ya esta implementado Multiples cuentas por usuario.

Permitir múltiples usuarios por cuenta,  se debe tener al menos dos roles dentro de account, el role de  owner de la cuenta y  una con otro Rol (que en el futuro limite por ejemplo la vista de factura, o de adicionar usuarios y cambiar los roles dentro del tenant, etc)

El rol Owner tendria acceso en  el dashboard al area de administración

### Usar las url con slug como url por default en lugar del ID. [Mac]

Ya en Cenit se soportan las url con slug y ademas de las id, en adicion seria conveniente que las url predeterminadas en la documentacion sean con slug. Esto ademas ayudaria a que sean indexadas por los motores de busqueda.

### Eliminar ‘setup~’ prefijo de las url. [Mac]

Todas las url tienen el prefijo 'setup~' que lo toma rails_admin de la carpeta setup. eliminar este prefijo que no cumple funcion.



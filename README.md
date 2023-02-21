
# Modelo MVC

Un modelo de datos es una representación visual de elementos de datos y las relaciones entre ellos. Es el método fundamental utilizado para aprovechar la abstracción en un sistema de información. Los modelos de datos definen la estructura lógica de los datos, cómo se conectan y cómo se procesan y almacenan los datos en los sistemas de información.
## Ejemplo modelo MVC JavaScript
```bash
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>MVC en Javascript, parte 1: Controladores</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
      <base href="http://localhost/lab/" />
      <link rel="stylesheet" type="text/css" href="css/cupertino/jquery-ui-1.8.7.custom.css" />
      <script type="text/javascript" src="js/jquery-1.4.4.min.js"></script>
      <script type="text/javascript" src="js/jquery-ui-1.8.7.custom.min.js"></script>
      <script type="text/javascript" src="js/jquery.address.min.js"></script>
    <script type="text/javascript">         
         $(document).ready(function () 
         {   
            var Tabs = $( "#tabs" );
            
            Tabs.tabs();
            
            $('#tabs a').click(function()
            { 
               url = $(this).attr('href').replace(/^.*#/, '');
               
               $.address.value(url);
            });

            $.address.change(function(event)
            {  
               tabUrl = event.value.replace(/^\//, '');
               Tabs.tabs("select", tabUrl);
            });
            
         });
      </script>
  </head>
  <body>
      <div class="demo">

         <div id="tabs">
            <ul>
               <li><a href="#ruylopez">Ruy Lopez</a></li>
               <li><a href="#siciliana">Siciliana</a></li>
               <li><a href="#gambitoderey">Gambito de rey</a></li>
            </ul>
            <div id="ruylopez">
               <p>Parrafo 1 ajedrez:</p>
               <p><strong>1.e4 e5 2.Cf3 Cc6 3.Ab5</strong></p>
               <p>Parrafo 2 ajedrez.</p>
               <p>EParrafo 3 ajedrez.</p>
            </div>
            <div id="siciliana">
               <p>Parrafo 1 siciliana.</p>
               <p>Parrafo 2 siciliana</p>
               <p>Parrafo 3 siciliana</p>
            </div>
            <div id="gambitoderey">
               <p>Parrafao 1 gambitoderey <strong>1.e4 e5 2.f4</strong></p>
               <p>Parrafo 2 gambitoderey.</p>
               <p>Parrafo 3 gambitoderey.</p>
            </div>
         </div>

      </div>
  </body>
</html>
```
# Funcionalidades de una app
### -Usabilidad
Cualquier app debe presentar una interfaz fácil e intuitiva que permita al usuario hacer uso de ella de forma cómoda.
### -Notificaciones inteligentes
Mantener un contacto periódico con los usuarios a través de las notificaciones inteligentes.
### -Seguridad
Ofrecer protección e invulnerabilidad es esencial para garantizar una buena ejecución de la aplicación.
### -Geolocalización
Conseguiremos impactar con gran eficacia sobre nuestro público objetivo.
### -Interacción
Conocer cómo mejorar la plataforma o qué características potenciar para conseguir mejores resultados.
### -Analítica
Adaptar sus características a las necesidades del mercado y tener en cuenta las funcionalidades básicas que deben adoptar para obtener éxito.

# Infraestructura para el almacenamiento y recuperación de datos
Los ordenadores o terminales modernos se conectan a dispositivos de almacenamiento, ya sea directamente o a través de una red. Los usuarios indican a los ordenadores que accedan a los datos y los almacenen en estos dispositivos de almacenamiento. A un nivel básico, los pilares básicos del almacenamiento de datos son dos: la forma que toman los datos y los dispositivos en los que se registran y almacenan.

### Javascript de almacenamiento local
```bash
  localStorage.setItem('user_name', 'Rohit'); //store a key/value
var retrievedUsername = localStorage.getItem('user_name'); //retrieve the key
```
### Almacenamiento local
```bash
// localStorage for objects, arrays or any data type
var obj = 
	firstName: "Bob",
    lastName: "Jeff",
    age: 13
localStorage.setItem("itemname", JSON.stringify(obj)); // Save the obj as string
var item = JSON.parse(localStorage.getItem("itemname")); 
// ^^ Parse string then set `item` as the obj
```
### Guardar en el almacenamiento local
```bash
var cat = localStorage.getItem('myCat');
```
# Modelo Vista Controlador (Vistas)
## Modelo
El modelo define qué datos debe contener la aplicación. Si el estado de estos datos cambia, el modelo generalmente notificará a la vista (para que la pantalla pueda cambiar según sea necesario) y, a veces, el controlador (si se necesita una lógica diferente para controlar la vista actualizada).

Volviendo a nuestra aplicación de lista de compras, el modelo especificará qué datos deben contener los artículos de la lista (artículo, precio, etc.) y qué artículos de la lista ya están presentes.
## Vista
La vista define cómo se deben mostrar los datos de la aplicación.

En nuestra aplicación de lista de compras, la vista definiría cómo se presenta la lista al usuario y recibiría los datos para mostrar desde el modelo.
## Controlador
El controlador contiene una lógica que actualiza el modelo y/o vista en respuesta a las entradas de los usuarios de la aplicación.

Entonces, por ejemplo, nuestra lista de compras podría tener formularios de entrada y botones que nos permitan agregar o eliminar artículos. Estas acciones requieren que se actualice el modelo, por lo que la entrada se envía al controlador, que luego manipula el modelo según corresponda, que luego envía datos actualizados a la vista.

Sin embargo, es posible que también se desee actualizar la vista para mostrar los datos en un formato diferente, por ejemplo, cambiar el orden de los artículos de menor a mayor precio o en orden alfabético. En este caso, el controlador podría manejar esto directamente sin necesidad de actualizar el modelo.

# En conclusión
Las tres partes del patrón de diseño de software MVC se pueden describir de la siguiente manera:

Modelo: Maneja datos y lógica de negocios.
Vista: Se encarga del diseño y presentación.
Controlador: Enruta comandos a los modelos y vistas.

# Modelo vista controlador (Controlador).
Se encarga de... controlar, recibe las órdenes del usuario y se encarga de solicitar los datos al modelo y de comunicárselos a la vista.
El Controlador como que “conoce la Vista”. Sabe a qué Vista debe dirigir el control, pero no sabe nada sobre esa Vista. Tampoco sabe de qué Vista provino el control anteriormente. El Controlador responde a los eventos. Un evento viene de la UI, llevando algún tipo de información de estado (un ViewModel, tal vez), dirige el control lógico a través de los Modelos (donde ocurre la lógica de negocio), y responde con un Modelo (o un ViewModel, si la forma de los datos específicos de una Vista particular es diferente a los Modelos) y una Vista.



##**SEBuscador Frontend**
SEBuscador Frontend es un complemento visual desarrollado para implementar de forma agil un buscador de elmentos geograficos en las aplicaciones desarrolladas por el departamento de tecnologia de SIGIS 

###**Requerimientos en el Servidor (Para desarrolladores)**

 * node js
 * npm
 * gulp

###**Dependencias**

 * jquery >= 1.9.0
 * IGV
 * Autocomplete, https://goodies.pixabay.com/jquery/auto-complete/demo.html
 * Multi Select, http://hemantnegi.github.io/jquery.sumoselect/

###**Instalacion**

 * Para desarrollar
 
  * Clonamos el repositorio

   ```sh
   
   svn checkout --Revision http://svn1.sigis.com.ve/buscador/buscador-elasticsearch/SBEfrontend
   
   ```
   * Instalamos los modulos node para generar documentacion y los archivos min
   
  ```sh
  
   $ cd tu-wokspace/SBEfrontend/
   $ npm install
   
  ```
  
   * Correr tareas gulp para la documentacion y minsear los archivos
   
   ```sh
   
   $ cd tu-wokspace/SBEfrontend/
   $ gulp
   
   ```

* Para Implementar en aplicaciones
 
  * Agergamos el repositorio como un external a nuetros proyecto.

   ```sh
   svn propget svn:externals nombreMiProyecto/algun-directorio sub-directorio-de-los-external http://svn1.sigis.com.ve/buscador/buscador-elasticsearch/SBEfrontend
   ```
   
  * Inclusión de el plugin en el header de la aplicacion
   
   ```html
   
      <header>
         <link href="ruta-css-de-tuproyecto/sumoselect.css" rel="stylesheet">
         <link href="ruta-css-de-tuproyecto/jquery.auto-complete.css" rel="stylesheet">
         <link type="text/css" rel="stylesheet" href="ruta-del-external-tuproyecto/SBEfrontend/dist/css/plugin-buscador.min.css" />
         
        <scritp src="jquery.js?v1.9.1" type="javscript" ></script>
        <script src="ruta-js-de-tuproyecto/jquery.sumoselect.min.js" ></script>
        <script src="ruta-js-de-tuproyecto/jquery.auto-complete.min.js" ></script
        <scritp src="ruta-del-external-tuproyecto/igv/igv.core.min.js" type="javscript" ></script>
        <scritp src="ruta-del-external-tuproyecto/SBEfrontend/dist/js/plugin-buscador.min.js" type="javscript" ></script>
      </header>
   
   ```

###**Uso**

- Inclusón de componentes visuales para realizar busquedas geograficas

   ```javascript
   
      var SBEconf = {
       container_id:'El-id-del-div',
       API:'http://jlara.webserver2a-local.sigis.com.ve:9090/',
       client:{
            grant_type:'client_credentials',
            client_id: 'el-id-cliente',
            client_secret: 'la-llave-secrete-del-cliente'
       }
      }
      
      SBE(SBEconf).mountComponents({map : instancia-del-mapa, path : 'ruta-donde-colocaste-el-SBEfrontend/dist'});
      
   ```

- Instanciando los metodos para consumir el API buscador

   ```javascript
   
      var SBEconf = {
       container_id:'El-id-del-div',
       API:'http://jlara.webserver2a-local.sigis.com.ve:9090/',
       client:{
            grant_type:'client_credentials',
            client_id: 'el-id-cliente',
            client_secret: 'la-llave-secrete-del-cliente'
       }
      }
      
      var promise = SBE(SBEconf).request();
      
      var success = function(result){
           console.log('la respuesta de la peticion',result)
      }
      
      promise.find('Caracas',success);
      
   ```

###**Opciones**

- SBE

  * **container_id:** este atributo alamcena el identifcador del contendor donde se van a cargar los componentes visuales. por defecto el utiliza el identificador **"buscador-container"**.
  
  * **API:** Este atributo almacena la ruta de los servicios, este valor es requerido si no lo pasa no arrancar el plugin.
  
  * **client:**Este atributo es de tipo objeto y almacena los datos de acceso de la aplicacion, esta informacion es requerida de lo contrario no podra inicializar el plugin. Observe los ejemplos de uso para que se familiarize con la estructura de este atributo
  
- mountComponents

  * **map:** Este atributo almacena la instancia del mapa, esta opcion es requerida para el correcto funcionamiento del plugin
  
  * **path:** Este atributo almacena la ruta absoluta donde se encuentra ubicado el directorio con los archivo de imagnes y componentes igv del plugin, por defecto el plugin tomara como ruta absoluta la siguiente si usted no la carga **"external/buscador-elasticsearch/SBEfrontend/dist/"** 
  
  * **resultsTemplate:** Este atributo permite modificar el la estructura como se muestran los reslutados, para esto debe la estructura de las respuesta de los servicios de busquedad para indicar los datos que desea mostrar en su diseño, para poder imprimir la informacion de los datos devuletos por el servicio en su diseño debe encerrar el nombre de la variable entre llaves como se muetra en el siguiente ejemplo.
  ```javascript
  
      SBE(SBEconf).mountComponents({
                                      map : instancia-del-mapa, 
                                      path : 'ruta-donde-colocaste-el-SBEfrontend/dist',
                                      resultsTemplate:'<p style="color:red" >{name}</p>'
                                   });
       
   
   ```
   
 
  * **popupTemplate:** Este atributo al igual que el resultsTemplate permite cambiar la presentacion de la nube que se muestra al dar click sobre el punto del elemnto en el mapa, la forma de armar es parecida a la descrita en resultsTemplate
  
  * **size:** Este atributo permite cambniar la cantidad de resultados que se muetran por peticion
  

###**Notas**


##**SEBuscador Frontend**
SEBuscador Frontend es un complemento visual desarrollado para implementar de forma agil un buscador de elmentos geograficos en las aplicaciones desarrolladas por el departamento de tecnologia de SIGIS 

###**Requerimientos en el Servidor (Para desarrolladores)**

 * node js
 * npm
 * gulp

###**Dependencias**

 * jquery >= 1.9.0
 * IGV

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
   
   ```
   
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
        <link type="text/css" rel="stylesheet" href="ruta-del-external-tuproyecto/SBEfrontend/plugin-buscador.min.css" />
        <scritp src="jquery.js?v1.9.1" type="javscript" ></script>
        <scritp src="ruta-del-external-tuproyecto/igv/igv.core.min.js" type="javscript" ></script>
        <scritp src="ruta-del-external-tuproyecto/SBEfrontend/plugin-buscador.min.js" type="javscript" ></script>
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
      
      SBE(SBEconf).mountComponents({map : instancia-del-mapa});
      
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

###**Notas**

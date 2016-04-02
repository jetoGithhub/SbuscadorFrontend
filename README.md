
##**SBuscador Frontend**
SBuscador Frontend es un complemento visual desarrollado para implementar de forma agil un buscador de elmentos geograficos en las aplicaciones desarrolladas por el departamento de tecnologia de SIGIS 

###**Instalacion**

 * Para desarrollar
 
  * Clonamos el repositorio

   ```sh
    svn checkout --Revision hombreMiProyecto/algun-directorio sub-directorio-de-los-external http://svn1.sigis.com.ve/buscador/buscador-elasticsearch/SBEForntend
   ```

* Para Implementar en aplicaciones
 
  * Agergamos el repositorio como un external a nuetros proyecto.

   ```sh
   svn propget svn:externals my-project/some-dir
   subdir http://svn.example.com/projects/my-project/external-dir
   ```
   
  * Inclusión de el plugin en el header de la aplicacion
   
   ```html
   <header>
     <link type="text/css" rel="stylesheet" href="ruta-del-external-tuproyecto/SBEForntend/plugin-buscador.min.css" />
     <scritp src="jquery.js?v1.9.1" type="javscript" ></script>
     <scritp src="ruta-del-external-tuproyecto/igv/igv.core.min.js" type="javscript" ></script>
     <scritp src="ruta-del-external-tuproyecto/SBEForntend/plugin-buscador.min.js" type="javscript" ></script>
   </header>
   ```
###**Uso**
- Inclusón de componentes visuales para realizar busquedas geograficas

```javascript
 
 ```
 - Instanciando los metodos para consumir el API buscador
```javascript
 
 ```
###**Optiones**

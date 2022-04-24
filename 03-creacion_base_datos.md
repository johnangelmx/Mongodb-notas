# Creacion de bases de datos

## use <nombre_base_datos>

Nos permite crear una base de datos. Y nos permite conectarnos a una base de datos.

### Notas en la creacion de base de datos:

Pasa una situacion al momento de elabora una base con use, el cual dicta que no sera visualizada por el comando `show dbs` , y esto ocurre porque mongo db no guarda una base nueva si no tiene una coleccion dentro.

### Insertando datos al crear una base de datos:

Para ello nos deberemos situar en la base de datos en la cual insertaremos datos con el comando `use <nombre_base_datos>`.

Una vez dentro de la base de datos, para asegurar que estamos dentro de ella, utilizamos el comando `db` y como resultado nos debe aparacer `<nombre_base_datos>`.

Ejemplificando que insertaremos una "coleccion" y un "documento" llamada **'products'**, utilizaremos el siguiente comando:  
`db.products.insert({'name':'laptop'})`  
Y como resultado obtendremos el siguiente mensaje:  
`WriteResult({ "nInserted" : 1 })`  
Y tambien podremos ver que la base de datos se creo con exito.
`show dbs`

## show collections

Nos permite ver las colecciones que tenemos dentro de la base de datos.

# Eliminar Base de Datos

## db.dropDatabase()

Nos permite eliminar la base de datos. Dando como resultado `{ "ok" : 1 }`

# Creando colecciones

En el apartado anterior de forma practica pudimos crear una base de datos , insertar una coleccion y un documento dentro de ella. y luego eliminar la base de datos.

Pero para poder insertar colecciones sin necesidad de insertar un documento podemos utilizar el comando `db.createCollection('<nombre_de_la_coleccion>')` , este nos permite crear una coleccion dentro de la base de datos.

Por ejemplo:  
`db.createCollection('users')`  
Y como respuesta obtendremos un:  
`{ "ok" : 1 }`  
Y a su vez podremos tipear el comando `show collections` para ver que se creo la coleccion.

# Eliminar una coleccion

Para poder eliminar una coleccion unica podremos utilizar el comando:  
 `db.<nombre_de_la_coleccion>.drop()`  
Este nos permite eliminar una coleccion dentro de la base de datos.

Y como resultado obtendremos un:  
`true` si fue eliminada con exito.  
`false` si no fue eliminada.

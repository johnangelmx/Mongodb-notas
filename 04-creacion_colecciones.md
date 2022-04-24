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

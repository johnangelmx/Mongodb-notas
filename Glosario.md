# Glosario

En este apartado se tratara de explicar y aplicar a los conmando internos del lenguaje.

## db

Nos permite ver la base de datos en donde nos situamos, y por defecto si no hemos ingresado a una ,por defecto nos conecta a la base test, que es una base de datos temporal.

## show dbs

Nos permite visualizar las bases de datos que tenemos en nuestra máquina.

## help

Nos muestra los comando que podemos utilizar.

## db.help()

Nos muesta todos los metodos que podemos utilizar en la base de datos.

## use <nombre_base_datos>

Nos permite crear una base de datos. Y nos permite conectarnos a una base de datos.

## show collections

Nos permite ver las colecciones que tenemos dentro de la base de datos.

## db.dropDatabase()

Nos permite eliminar la base de datos. Dando como resultado `{ "ok" : 1 }`

## db.createCollection('<nombre_de_la_coleccion>')

Este nos permite crear una coleccion dentro de la base de datos.

## db.<nombre_de_la_coleccion>.drop()

Este nos permite eliminar una coleccion dentro de la base de datos.

## db.<nombre_de_la_coleccion>.insert(document)

Nos permite ingresar un documento dentro de la coleccion.

## db.<nombre_de_la_coleccion>.insert(<cuerpo_del_documento>)

Nos permite ingresar de manera directa una coleccion y el cuerpo del documento en una sola instruccion

## db.<nombre_de_la_coleccion>.find()

Nos permite visualizar los documentos dentro de la coleccion seleccionada

## db.<nombre_de_la_coleccion>.find().pretty()

Nos permite visualizar de una manera mas estetica los documentos dentro de la coleccion selccionada

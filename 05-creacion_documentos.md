# Creacion de documentos

En los apartados anteriores pudimos ver la jerarquia dentro de una base de datos mongodb, la cual nos dicta de la siguiente forma:

- db
  - collection
    - document

## Pero, Que formato tiene un documento?

```
{
  "nombre": "laptop",
  "precio": 40.2,
  "active": false,
  "created_at": new Date("12/12/2012"),
  "somedata": [1, "a", []],
  "factucturer": {
    "name": "Dell",
    "country": "USA",
    "version": "XPS",
    "location": {
      "city": "San Jose",
      "state": "California",
      "zip": "95131"
    }
  }
}
```

Como podemos observar, el formato de un documento es un objeto JSON,el cual nos permite ingresar desde diferentes tipo de datos hasta otros documentos dentro de un documento.

## Ahora bien, Como añadimos un documento a una base de datos?

Hay una forma directa de hacerlo , es decir , utilizando el comando `db.collection.insert(document)` , este nos permite insertar un documento dentro de una coleccion y crear la coleccion de una manera directa.

Por ejemplo , si nosotros queremso insertar a la base de datos lo anterior escrito y que la coleccion tambien se inserte, lo haremos de la siguiete forma:  
Dentro de la shell:

```
db.products.insert({
...   "nombre": "laptop",
...   "precio": 40.2,
...   "active": false,
...   "created_at": new Date("12/12/2012"),
...   "somedata": [1, "a", []],
...   "factucturer": {
...     "name": "Dell",
...     "country": "USA",
...     "version": "XPS",
...     "location": {
...       "city": "San Jose",
...       "state": "California",
...       "zip": "95131"
...     }
...   }
}...})
```

Como resultado obteniendo un

```
WriteResult({ "nInserted" : 1 })
```

## Visualizando un documento

Una vez ingresado los datos de manera directa podemos visualizarlo con el comando `db.collection.find()` , este nos permite visualizar todos los documentos de una coleccion.  
Teniendo como resultado:

```
db.products.find()
{ "_id" : ObjectId("6264ac96e46c0ce2c39c776d"), "nombre" : "laptop", "precio" : 40.2, "active" : false, "created_at" : ISODate("2012-12-12T06:00:00Z"), "somedata" : [ 1, "a", [ ] ], "factucturer" : { "name" : "Dell", "country" : "USA", "version" : "XPS", "location" : { "city" : "San Jose", "state" : "California", "zip" : "95131" } } }
```

Pero como podemos observar, el resultado es poco legible y no es muy facil de entender. Por ellos podremos utilizar el comando `db.collection.find().pretty()` , este nos permite visualizar los documentos de una coleccion de manera mas legible.  
Teniendo como resultado:

```
{
        "_id" : ObjectId("6264ac96e46c0ce2c39c776d"),
        "nombre" : "laptop",
        "precio" : 40.2,
        "active" : false,
        "created_at" : ISODate("2012-12-12T06:00:00Z"),
        "somedata" : [
                1,
                "a",
                [ ]
        ],
        "factucturer" : {
                "name" : "Dell",
                "country" : "USA",
                "version" : "XPS",
                "location" : {
                        "city" : "San Jose",
                        "state" : "California",
                        "zip" : "95131"
                }
        }
}
```

Y como podemos visualizar el resultado es un tanto diferente a lo que ingresamos , como la inserccion de un id dentro del dcoumento, este id es creado automaticamente por mongodb, el cual tiene un proceso interno que se asegura que el id es unico dentro de la base de datos, a su vez otro cambio significativo es la fecha de creacion del documento el cual nosotros ingresamos con una funcion de js `new Date()` pero mongodb cambia de formato ingresdo `ISODate("2012-12-12T06:00:00Z")` , este con finalidad que el mismo lo entienda dentro de su base de datos.

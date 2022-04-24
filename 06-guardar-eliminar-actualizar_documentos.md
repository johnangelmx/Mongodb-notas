# Operaciones en mongoDB

Ejemplificando el uso de los metodos en mongoDB el siguiente ejemplo engloba la operacion de guardar, eliminar, actualizar y consultar documentos.

### Creando la base de datos

```
use mystore
```

### Creando las colecciones

```
db.createCollection("products")
```

### Insertar un documento en la coleccion

```
db.products.insert({'name': 'keyboard'})
```

### Inserta un documento con 2 campos en la coleccion

```
db.producst.insert({'name': 'laptop', 'price': 999.99 })

```

### Inserta un documento con multiples campos en la coleccion

```
db.products.insert([
    {
        "name": "mouse",
        "description": "razer mouse",
        "tags": [
            "computers",
            "gaming"
        ],
        "quantity": 14,
        "created_at": new Date(),
    },
    {
        "name": "monitor",
        "description": "LG monitor",
        "tags": [
            "computers",
            "gaming"
        ],
        "quantity": 3,
        "created_at": new Date(),
    }
])

```

# Consultando un documento

Ahora bien , como hemos aprendido en recursos anteriores se puede consultar un documento en la coleccion con el comando `db.collection.find()`y estilizarlo con el comando `db.collection.find().pretty()` dando como resultado lo siguiente:

```
{ "_id" : ObjectId("6264d3083482bfb689f33626"), "name" : "keyboard" }
{
        "_id" : ObjectId("6264d3273482bfb689f33628"),
        "name" : "mouse",
        "description" : "razer mouse",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 14,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
{
        "_id" : ObjectId("6264d3273482bfb689f33629"),
        "name" : "monitor",
        "description" : "LG monitor",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 3,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
{
        "_id" : ObjectId("6264d50f3482bfb689f3362c"),
        "name" : "laptop",
        "price" : 999.99
}
```

Parte de que podamos visualizar los documentos que tenemos en la coleccion es gracias a la funcion `db.collection.find()` pero el `.find()` nos permite filtrar los documentos que queremos consultar, por ejemplo:  
Si necesitamos buscar algun documento por su nombre, en este caso un objeto por su nombre podemos hacerlo de la siguiente manera:

```
db.products.find({'name': 'keyboard'})
```

Teniendo como resultado:

```
{ "_id" : ObjectId("6264d3083482bfb689f33626"), "name" : "keyboard" }
```

Devolviendo asi la consulta de un documento por su nombre.  
Se puede ejemplificar de esta forma:

```
db.products.find({'price': 999.99})
```

Teniendo como resultado:

```
{ "_id" : ObjectId("6264d50f3482bfb689f3362c"), "name" : "laptop", "price" : 999.99 }
```

Demostrando asi el uso de cualquier tipo de dato con el metodo `.find()`

## Pero , que pasa con la busqueda de propiedades que tienen un arreglo o un objeto dentro de ellos?

Para ello el metodo `.find()`nos permite hacer la busqueda de una propiedad que contenga un arreglo o un objeto dentro de ella, por ejemplo:

```
db.products.find({"tags": "computers"}).pretty()
```

Dando como resultado:

```
{
        "_id" : ObjectId("6264d3273482bfb689f33628"),
        "name" : "mouse",
        "description" : "razer mouse",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 14,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
{
        "_id" : ObjectId("6264d3273482bfb689f33629"),
        "name" : "monitor",
        "description" : "LG monitor",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 3,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
```

Demostrando asi que no importa si esta dentro de un arreglo u otro documento(objeto), este se puede buscar.

## Filtrando mas de una propiedad

El metodo `.find()` nos permite filtrar mas de una propiedad, por ejemplo:

```
db.products.find({"tags": "computers", "name": "monitor"}).pretty()
```

Dando como resultado:

```
{
        "_id" : ObjectId("6264d3273482bfb689f33629"),
        "name" : "monitor",
        "description" : "LG monitor",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 3,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
```

Permitiendo asi filtrar mas de una propiedad para encontrar el documento que cumpla con estas condiciones.

# .FindOne()

El metodo `.findOne()` nos permite buscar un documento en la coleccion, pero solo nos devuelve un documento, no un arreglo de documentos.

```
db.products.findOne({"tags": "computers"}).pretty()
```

Como resultado:

```
{
        "_id" : ObjectId("6264d3273482bfb689f33628"),
        "name" : "mouse",
        "description" : "razer mouse",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 14,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
```

# Obteniendo determinadas propiedades de un documento

Una forma de visualizar determinadas propiedades de un documento es de la siguiente manera:

```
db.products.findOne({"tags": "computers"},{'name': 1, 'description': 1})

```

Teniendo como resultado

```
{
        "_id" : ObjectId("6264d3273482bfb689f33628"),
        "name" : "mouse",
        "description" : "razer mouse"
}
```

Pero aun podemos ver que el id nos lo muestra, pero no lo queremos, por eso podemos hacer lo siguiente:

```
db.products.findOne({"tags": "computers"},{'name': 1, 'description': 1, '_id': 0})

```

Teniendo como resultado

```
{
        "name" : "mouse",
        "description" : "razer mouse"
}
```

# .sort()

El metodo `.sort()` nos permite ordenar los documentos de una coleccion, por ejemplo:

```
db.products.find({'tags': 'computers'}).sort({'name': 1})
```

Teniedo como resultado:

```
{
        "_id" : ObjectId("6264d3273482bfb689f33629"),
        "name" : "monitor",
        "description" : "LG monitor",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 3,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
{
        "_id" : ObjectId("6264d3273482bfb689f33628"),
        "name" : "mouse",
        "description" : "razer mouse",
        "tags" : [
                "computers",
                "gaming"
        ],
        "quantity" : 14,
        "created_at" : ISODate("2022-04-24T04:33:43.435Z")
}
```

# .limit()

El metodo `.limit()` nos permite limitar la cantidad de documentos que se muestran en la coleccion, por ejemplo:

```
db.products.find().limit(2)
```

Devolviendo asi unicamente 2 datos:

```
{ "_id" : ObjectId("6264d3083482bfb689f33626"), "name" : "keyboard" }
{ "_id" : ObjectId("6264d3273482bfb689f33628"), "name" : "mouse", "description" : "razer mouse", "tags" : [ "computers", "gaming" ], "quantity" : 14, "created_at" : ISODate("2022-04-24T04:33:43.435Z") }
```

# .count()

El metodo `.count()` nos permite contar la cantidad de documentos que hay en la coleccion, por ejemplo:

```
db.products.find().count()
```

Dando como resltado:

```
4
```

# .forEach()

El metodo `.forEach()` nos permite iterar sobre los documentos de una coleccion, por ejemplo:

```
db.products.find().forEach(product=> print("Product Name: " + product.name))
```

Teniendo como resultado:

```
Product Name: keyboard
Product Name: mouse
Product Name: monitor
Product Name: laptop
```

# Actualizar un documento

El metodo `.update()` nos permite actualizar un documento en la coleccion, por ejemplo:

```
db.products.update({"name": "keyboard"}, {'price': 99.99})

```

como resultado:

```
{ "_id" : ObjectId("6264d3083482bfb689f33626"), "price" : 99.99 }
```

Viendo asi que no agrego ninguna propiedad, pero si actualizo la propiedad

# Agregar una propiedad en un documento

Para poder agregar una propiedad en un documento, debemos usar el metodo `.update()` con una condicion esta condicion tendra el metodo `$set`, por ejemplo:

```
db.products.update({"name": "laptop"}, {'$set': {'description': 'lg gram laptop'}})

```

El apartdo `$set` nos permite agregar una propiedad en un documento, sin necesidad de actualizar el documento completo y volverlo a sobrescribir todas sus propiedades.

El apartado `$inc` nos permite incrementar una propiedad en un documento  
El apartado `$unset` nos permite eliminar una propiedad en un documento  
El apartado `$push` nos permite agregar una propiedad en un documento  
El apartado `$pull` nos permite eliminar una propiedad en un documento  
El apartado `$rename` nos permite renombrar una propiedad en un documento

# Eliminar un documento

El metodo `.remove()` nos permite eliminar un documento en la coleccion, por ejemplo:

```
db.products.remove({"name": "keyboard"})

```

Teniendo como resultado la eliminacion del documento

# Eliminar todos los documentos

El metodo `.remove()` nos permite eliminar todos los documentos de una coleccion, por ejemplo:

```
db.products.remove({})

```x

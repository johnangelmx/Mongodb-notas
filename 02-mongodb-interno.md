# ESTRUCTURA DE DATOS

La estructura de MongoDB es jerárquica, y consta de los siguientes niveles:
- **Base de datos (database)**: sirve como contenedor para las colecciones. Normalmente se almacenan colecciones relacionadas con la misma aplicación. Cada base de datos puede contener varias colecciones.
- **Colecciones (collections)**: almacenan registros individuales, también llamados documentos. Permite agrupar elementos que sean similares.Las colecciones en MongoDB son como tablas en una base de datos SQL, pero son grupos de documentos en lugar de grupos de registros
- **Documentos (documents)**: el término documento se refiere a la forma en que los datos son encapsulados y codificados. MongoDB usa el formato BSON (Binary JSON) para almacenar la información, aunque luego la muestra como JSON. El equivalente al término documento en bases de datos relacionales es el de fila. Cada documento contiene el nombre del dato y su contenido. Los documentos permiten anidación, por lo que un mismo documento puede representar un conjunto entero de datos de diferente naturaleza. No es necesario, por tanto, dividir los datos en distintas tablas como en las bases de datos relacionales de forma que luego sea necesario cruzarlas para obtener la entidad completa. MongoDB también permite que la estructura de los documentos en una misma colección sea distinta, permitiendo que unos documentos tengan más campos que otros por ejemplo. No obstante, los documentos tienen una limitación de 16Mb.
- **Índices (indexes)**: un índice es una estructura especial de datos que almacena una pequeña porción del conjunto de datos de las colecciones. Esta estructura se puede recorrer de forma muy rápida, y ayuda a agilizar las consultas a la base de datos. Por defecto, MongoDB indexa el _id de los documentos.

# TIPOS DE DATOS
La información de los documentos puede estar almacenada en los siguientes tipos de datos:

- Tipos simples:
    - **string**: tipo de dato de cadena de texto
    - **int32**: número entero de 32bit
    - **double**: número de coma flotante. Hay que tener en cuenta que las operaciones aritméticas sobre números de coma flotante puede ser imprecisa para ciertos tipos de aplicaciones
    - **decimal**: número decimal para casos en los que se necesita gran precisión en operaciones aritméticas (con datos financieros, por ejemplo)
    - **date**: tipo de dato para fecha/hora
- Tipos compuestos:
    - **document**: MongoDB permite el anidado de documentos, que a su vez pueden estar formados por tipos simples o por más documentos
    - **Array**: permite el uso de tablas con posiciones indexadas que contentan un número variable de datos
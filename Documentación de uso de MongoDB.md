# Un documento de MongoDB
Los registros en una base de datos __MongoDB__ se denominan documentos y los valores de los campos pueden incluir números,cadenas,valores booleanos, matrices o incluso documentos anidados.

_Documento de ejemplo:_
~~~
{
  title: "Post Title 1",
  body: "Body of post.",
  category: "News",
  likes: "1",
  tags:["News","Events"],
  date: Date()
}
~~~

# MongoDB 
__MongoDB__ es una base de datos de documentos y puede instalarse localmente o alojarse en la nube.

## SQL frente a bases de datos de documentos
Las bases de datos SQL se consideran bases de datos relacionales. Almacenan datos relacionados en tablas separadas. Cuando se necesitan datos, se consultan desde varias tablas para volver a unirlos.

MongoDB es una base de datos de documentos a la que a menudo se hace referencia como base de datos no relacional. Esto no significa que los datos relacionales no puedan almacenarse en bases de datos de documentos. Significa que los datos relacionales se almacenan de manera diferente. Una mejor manera de referirse a ella es como base de datos no tabular.

MongoDB almacena datos en documentos flexibles. En lugar de tener varias tablas, simplemente puede mantener todos los datos relacionados juntos. Esto hace que la lectura de sus datos sea muy rápida.

También puedes tener varios grupos de datos. En MongoDB, en lugar de tablas, se les llama colecciones.



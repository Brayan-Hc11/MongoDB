# Taller Uno: Inicios en MongoSh (Primera parte)

## Proceso a ejecutar 

1.Como primer paso realizaremos Una base de datos con el nombre de "Store" y una colección llamada "Inventory", esto lo realizaremos desde el mongo compass.
para poder ver que la base de datos ha sido creada con exito ejecutaremos el siguiente comando en la terminal de MongoSh:`show databases;` o `show db;`

_Instrucción a ejecutar:_ `>show databases;`

En la terminal de MongoSh nos debera de saltar algo similar a esto:
~~~
>show databases:
< admin 40.00 KiB
  config 96.00 KiB
  Store 8.00 KiB
  local 72.00 KiB
  test 40.00 KiB
~~~
para usar nuestra base de datos "Store" usaremos el siguiente comando `use Store;`

_Instrucción a ejecutar:_ `>use Store;`

Como resultado en la terminal se nos debera de mostrar el siguiente dialogo:

~~~
>use Store;
<switched to db Store;
inventory;>
~~~

***
2.Ya creada nuestra base de datos lo que haremos será insertar datos en la colección, para realizar esta acción insertaremos las siguiestes instrucciones:

_Instrucción a ejecutar:_ `>db.inventory.insertMany()`
~~~
db.Inventory.insertMany([
  {item:"Journal",qty:25,tags:["Blank","Red"],dim_cm:[14,21]},
  {item:"Notebook",qty:50,tags:["Red","Blank"],dim_cm:[14,21]},
  {item:"Paper",qty:100,tags:["Red","Blank","Pain"],dim_cm:[14,21]},
  {item:"Planner",qty:75,tags:["Blank","Red"],dim_cm:[22.85,30]},
  {item:"Postcard",qty:45,tags:["Blue"],dim_cm:[10,15.25]}
]);
~~~

_Resultado de ejecución:_

~~~
db.Inventory.insertMany([
  {item:"Journal",qty:25,tags:["Blank","Red"],dim_cm:[14,21]},
  {item:"Notebook",qty:50,tags:["Red","Blank"],dim_cm:[14,21]},
  {item:"Paper",qty:100,tags:["Red","Blank","Pain"],dim_cm:[14,21]},
  {item:"Planner",qty:75,tags:["Blank","Red"],dim_cm:[22.85,30]},
  {item:"Postcard",qty:45,tags:["Blue"],dim_cm:[10,15.25]}
]);
<{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("6535694988ec4615fdd07f23"),
    '1': ObjectId("6535694988ec4615fdd07f24"),
    '2': ObjectId("6535694988ec4615fdd07f25"),
    '3': ObjectId("6535694988ec4615fdd07f26"),
    '4': ObjectId("6535694988ec4615fdd07f27")
  }
}
~~~

***
3.Realiza una consulta que logre Buscar los documentos que tengan en "dim_cm:" un valor entre 10 y 15.Para realizar esta consulta ingresasremos la siguiente instrucción: `db.Inventory.find();`, al interior de los parentesis esctibiremos las sentecias y los datos que queremso buscar, para este caso buscaremos los valores que se hayan entre 10 y 15 del atributo `dim_cm:` en la colección "Inventory"

_Instrucción a insertar:_

~~~
>db.Inventory.find({$and:[{"dim_cm":{$gt: 10}},{dim_cm:$lt: 15}]});
~~~

_Resultado de ejecución:_

~~~
>db.Inventory.find({$and:[{"dim_cm":{$gt: 10}},{dim_cm:$lt: 15}]});
<{
  _id: ObjectId("6535684488ec4615fdd07f22"),
  item: 'Journal',
  qty: 25,
  tags: [
    'Blank',
    'Red'
  ],
  dim_cm: [
    14,
    21
  ]
}
{
  _id: ObjectId("6535694988ec4615fdd07f23"),
  item: 'Journal',
  qty: 25,
  tags: [
    'Black',
    'Red'
  ],
  dim_cm: [
    14,
    21
  ]
}
{
  _id: ObjectId("6535694988ec4615fdd07f24"),
  item: 'Notebook',
  qty: 50,
  tags: [
    'Red',
    'Blank'
  ],
  dim_cm: [
    14,
    21
  ]
}
{
  _id: ObjectId("6535694988ec4615fdd07f25"),
  item: 'Paper',
  qty: 100,
  tags: [
    'Red',
    'Blank',
    'Pain'
  ],
  dim_cm: [
    14,
    21
  ]
}
{
  _id: ObjectId("6535694988ec4615fdd07f27"),
  item: 'postcard',
  qty: 45,
  tags: [
    'Blue'
  ],
  dim_cm: [
    10,
    15.25
  ]
}
Store>
~~~




 

 










# Taller Uno: Inicios en MongoSh (Segunda parte)

## Proceso a ejecutar 
1.Para esta sedunda parte como primer punto crearemos un base de datos llamada "Tienda" en la que se encontará una colección llamada "Telefonos".
para poder ver que la base de datos ha sido creada con exito ejecutaremos el siguiente comando en la terminal de MongoSh:`show databases;` o `show db;`

_Instrucción a ejecutar:_ `>show databases;`

En la terminal de MongoSh nos debera de saltar algo similar a esto:
~~~
>show databases:
< Store 72.00 KiB
  Tienda 40.00 KiB
  admin 40.00 KiB
  config 108.00 KiB
  local 72.00 KiB
  test 40.00 KiB
Tienda>
~~~
para usar nuestra base de datos "Store" usaremos el siguiente comando `use Tienda;`

_Instrucción a ejecutar:_ `>use Tienda;`

Como resultado en la terminal se nos debera de mostrar el siguiente dialogo:

~~~
>use Tienda;
<switched to db Tienda;
inventory;>
~~~

2.Al interio de la colección telefónos insertaremos los siguientes datos:

_Instrucción a insertar:_ `>db.Telefonos.insertMany();`

~~~
db.Telefonos.insertMany([
{"Name":"AC3 Phone","Brand":"ACME","Type":"Phone","Price":200,"Rating":3.8,"Warranty_Years":1,"Available":true},
{"Name":"AC7 Phone","Brand":"ACME","Type":"Phone","Price":320,"Rating":4,"Warranty_Years":1,"Available":false},
{"Name":"AC3 Series Changer","Type":["Accesory","Charger"],"Price":19,"Rating":2.8,"Warranty_Years":0.25,"For":["AC7","QP8","QP9"]},
{"Name":"AC3 Case Green","Type":["Accesory","Case"],"Color":"Green","Price":12,"Rating":1,"Warranty_Years":0},
{"Name":"Phone Extended Warranty", "Type":"Warranty","price":38,"Rating":5,"Warranty_Years":2,"For":["AC3","AC7","AC9","QP7","QP8","QP9"]},
{"Name":"AC3 Case Black","Type":["Accesory","Case"],"Color":"Black","Price":12.5,"Rating":2,"Warranty_Years":0.25,"Available":false,"For":"AC3"},
{"Name":"AC3 Case Red","Type":["Accesory","Case"],"Color":"Red","Price":12,"Rating":4,"Warranty_Years":0.25,"Available":true,"For":"AC3"},
{"Name": "Phone Service Basic Plan","Type":"Service","Monthly_price":40,"Rating":3,"Limits":{"Voice":{"Units": "Minutes", "N": 400, "Over_rate": 0.05},"Data":{"Units":"Gigabytes", "N":20,"Over_rate":1},"SMS":{"Units":"Text sent","N":100,"Over_rate":0.001 }},"Term_years":2},
{"Name": "Phone Service Core Plan","Type":"Service","Monthly_price":60,"Rating":3,"Limits":{"Voice":{"Units":"Minutes","N":1000,"Over_rate":0.05},"Data":{"N":"Unlimited", "Over_Rate":0},"SMS":{"N":"Unlimited","Over_rate":0}},"Term_years":1},
{"Name": "Phone Service Family Plan","Type":"Service","Monthly_price":90,"Rating":4,"Limits":{"Voice":{"Units":"Minutes","N":1200,"Over_rate":0.05},"Data":{"N":"Unlimited","Over_Rate":0},"SMS":{"N":"Unlimited","Over_rate":0}},"Sales_tax":true,"Term_years":2}
]);
~~~

_Resultado de ejecución:_

~~~
db.Telefonos.insertMany([
{"Name":"AC3 Phone","Brand":"ACME","Type":"Phone","Price":200,"Rating":3.8,"Warranty_Years":1,"Available":true},
{"Name":"AC7 Phone","Brand":"ACME","Type":"Phone","Price":320,"Rating":4,"Warranty_Years":1,"Available":false},
{"Name":"AC3 Series Changer","Type":["Accesory","Charger"],"Price":19,"Rating":2.8,"Warranty_Years":0.25,"For":["AC7","QP8","QP9"]},
{"Name":"AC3 Case Green","Type":["Accesory","Case"],"Color":"Green","Price":12,"Rating":1,"Warranty_Years":0},
{"Name":"Phone Extended Warranty", "Type":"Warranty","price":38,"Rating":5,"Warranty_Years":2,"For":["AC3","AC7","AC9","QP7","QP8","QP9"]},
{"Name":"AC3 Case Black","Type":["Accesory","Case"],"Color":"Black","Price":12.5,"Rating":2,"Warranty_Years":0.25,"Available":false,"For":"AC3"},
{"Name":"AC3 Case Red","Type":["Accesory","Case"],"Color":"Red","Price":12,"Rating":4,"Warranty_Years":0.25,"Available":true,"For":"AC3"},
{"Name": "Phone Service Basic Plan","Type":"Service","Monthly_price":40,"Rating":3,"Limits":{"Voice":{"Units": "Minutes", "N": 400, "Over_rate": 0.05},"Data":{"Units":"Gigabytes", "N":20,"Over_rate":1},"SMS":{"Units":"Text sent","N":100,"Over_rate":0.001 }},"Term_years":2},
{"Name": "Phone Service Core Plan","Type":"Service","Monthly_price":60,"Rating":3,"Limits":{"Voice":{"Units":"Minutes","N":1000,"Over_rate":0.05},"Data":{"N":"Unlimited", "Over_Rate":0},"SMS":{"N":"Unlimited","Over_rate":0}},"Term_years":1},
{"Name": "Phone Service Family Plan","Type":"Service","Monthly_price":90,"Rating":4,"Limits":{"Voice":{"Units":"Minutes","N":1200,"Over_rate":0.05},"Data":{"N":"Unlimited","Over_Rate":0},"SMS":{"N":"Unlimited","Over_rate":0}},"Sales_tax":true,"Term_years":2}
]);
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("653581b988ec4615fdd07f28"),
    '1': ObjectId("653581b988ec4615fdd07f29"),
    '2': ObjectId("653581b988ec4615fdd07f2a"),
    '3': ObjectId("653581b988ec4615fdd07f2b"),
    '4': ObjectId("653581b988ec4615fdd07f2c"),
    '5': ObjectId("653581b988ec4615fdd07f2d"),
    '6': ObjectId("653581b988ec4615fdd07f2e"),
    '7': ObjectId("653581b988ec4615fdd07f2f"),
    '8': ObjectId("653581b988ec4615fdd07f30"),
    '9': ObjectId("653581b988ec4615fdd07f31")
  }
}
~~~

***
3.Como tercer paso realizaremos unas consultas a la colección:

-  Como primera consulta debe consultar los elementos cuyo atributo "Type" sea igual al dato "Service"

_Instrucción a ejecutar:_ `db.Telefonos.find();`

~~~
>db.Telefonos.find({"Type":"Service"});
~~~

_Resultado de ejecución:_

~~~
>db.Telefonos.find({"Type":"Service"});
{
  _id: ObjectId("653581b988ec4615fdd07f2f"),
  Name: 'Phone Service Basic Plan',
  Type: 'Service',
  Monthly_price: 40,
  Rating: 3,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 400,
      Over_rate: 0.05
    },
    Data: {
      Units: 'Gigabytes',
      N: 20,
      Over_rate: 1
    },
    SMS: {
      Units: 'Text sent',
      N: 100,
      Over_rate: 0.001
    }
  },
  Term_years: 2
}
{
  _id: ObjectId("653581b988ec4615fdd07f30"),
  Name: 'Phone Service Core Plan',
  Type: 'Service',
  Monthly_price: 60,
  Rating: 3,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 1000,
      Over_rate: 0.05
    },
    Data: {
      N: 'Unlimited',
      Over_Rate: 0
    },
    SMS: {
      N: 'Unlimited',
      Over_rate: 0
    }
  },
  Term_years: 1
}
{
  _id: ObjectId("653581b988ec4615fdd07f31"),
  Name: 'Phone Service Family Plan',
  Type: 'Service',
  Monthly_price: 90,
  Rating: 4,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 1200,
      Over_rate: 0.05
    },
    Data: {
      N: 'Unlimited',
      Over_Rate: 0
    },
    SMS: {
      N: 'Unlimited',
      Over_rate: 0
    }
  },
  Sales_tax: true,
  Term_years: 2
}
~~~

- Como segunda consulta debe consultar los elementos cuyo atributo "Type" sea igual al dato "Service" y adicional a eso el atributo "Price" sea igual al dato "> 50"

 _Intrucción a ejecutar:_  `>db.Telefonos.find();`

~~~
>db.Telefonos.find({$and:[{"Type": "Service"},{"Monthly_price":{$gt: 50}}]});
~~~

_Resultado de ejecución:_ 

~~~
>db.Telefonos.find({$and:[{"Type":"Service"},{"Monthly_price":{$gt:50}}]});
{
  _id: ObjectId("653581b988ec4615fdd07f30"),
  Name: 'Phone Service Core Plan',
  Type: 'Service',
  Monthly_price: 60,
  Rating: 3,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 1000,
      Over_rate: 0.05
    },
    Data: {
      N: 'Unlimited',
      Over_Rate: 0
    },
    SMS: {
      N: 'Unlimited',
      Over_rate: 0
    }
  },
  Term_years: 1
}
{
  _id: ObjectId("653581b988ec4615fdd07f31"),
  Name: 'Phone Service Family Plan',
  Type: 'Service',
  Monthly_price: 90,
  Rating: 4,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 1200,
      Over_rate: 0.05
    },
    Data: {
      N: 'Unlimited',
      Over_Rate: 0
    },
    SMS: {
      N: 'Unlimited',
      Over_rate: 0
    }
  },
  Sales_tax: true,
  Term_years: 2
}
~~~

- Como tercera consulta debe consultar los elementos cuyo atributo "Type" sea igual al dato "Service" o  el atributo "Price" sea igual al dato "> 50"

_Intrucción a ejecutar:_  `>db.Telefonos.find();`

~~~
>db.Telefonos.find({$or:[{"Type": "Service"},{"Monthly_price":{$gt: 50}}]});
~~~

_Resultado de ejecución:_

~~~
>db.Telefonos.find({$or:[{"Type":"Service"},{"Monthly_price":{$gt:50}}]});
{
  _id: ObjectId("653581b988ec4615fdd07f2f"),
  Name: 'Phone Service Basic Plan',
  Type: 'Service',
  Monthly_price: 40,
  Rating: 3,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 400,
      Over_rate: 0.05
    },
    Data: {
      Units: 'Gigabytes',
      N: 20,
      Over_rate: 1
    },
    SMS: {
      Units: 'Text sent',
      N: 100,
      Over_rate: 0.001
    }
  },
  Term_years: 2
}
{
  _id: ObjectId("653581b988ec4615fdd07f30"),
  Name: 'Phone Service Core Plan',
  Type: 'Service',
  Monthly_price: 60,
  Rating: 3,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 1000,
      Over_rate: 0.05
    },
    Data: {
      N: 'Unlimited',
      Over_Rate: 0
    },
    SMS: {
      N: 'Unlimited',
      Over_rate: 0
    }
  },
  Term_years: 1
}
{
  _id: ObjectId("653581b988ec4615fdd07f31"),
  Name: 'Phone Service Family Plan',
  Type: 'Service',
  Monthly_price: 90,
  Rating: 4,
  Limits: {
    Voice: {
      Units: 'Minutes',
      N: 1200,
      Over_rate: 0.05
    },
    Data: {
      N: 'Unlimited',
      Over_Rate: 0
    },
    SMS: {
      N: 'Unlimited',
      Over_rate: 0
    }
  },
  Sales_tax: true,
  Term_years: 2
}
Tienda>
~~~





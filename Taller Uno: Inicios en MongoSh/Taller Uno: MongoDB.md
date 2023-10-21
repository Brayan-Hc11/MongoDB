# Taller Uno: Inicios en MongoSh 

## Proceso a ejecutar 

1.Como primer paso realizaremos Una base de datos con el nombre de "Inventory", esto lo realizaremos desde el mongo compass.
para poder ver que la base de datos ha sido creada con exito ejecutaremos el siguiente comando en la terminal de MongoSh:`show databases:` o `show db:`

_Resultado de la ejecución:_

En la terminal de MongoSh nos debera de mostrar algo similar a esto:
~~~
>show databases:
< admin 40.00 KiB
  config 96.00 KiB
  inventory 8.00 KiB
  local 72.00 KiB
  test 40.00 KiB
~~~
para usar nuestra base de datos "inventory" usaremos el siguiente comando `use invetory:`

_Resultado de ejecución:_

Como resultado en la terminal se nos debera de mostrar el siguiente dialogo
~~~
>use inventory:
<switched to db inventory:
inventory:>
~~~

***
2.Ya creada nuestra base de datos lo que haremos será insertar datos, para realizar esta acción insertaremos las siguiestes instrucciones:

~~~
db.inventory.insertMany([
  {item:"Journal",qty:25,tags:["Blank","Red"],dim_cm:[14,21]},
  {item:"Notebook",qty:50,tags:["Red","Blank"],dim_cm:[14,21]},
  {item:"Paper",qty:100,tags:["Red","Blank","Pain"],dim_cm:[14,21]},
  {item:"Planner",qty:75,tags:["Blank","Red"],dim_cm:[22.85,30]},
  {item:"Postcard",qty:45,tags:["Blue"],dim_cm:[10,15.25]}

]);
~~~












# Базоые возможности mongodb

**Задание**<br>
* установить MongoDB одним из способов: ВМ, докер;
* заполнить данными;
* написать несколько запросов на выборку и обновление данных Сдача ДЗ осуществляется в виде миниотчета

1. установка mongodb <br>
    `docker pull mongo (docker уже установлен)` <br>
    `docker run -it --rm --name mongodb -d mongo` <br>
    `docker exec -it mongodb mongo` <br><br>

2. заполнение данными <br>
   `use shop` <br>
   создание коллекции <br>
   `db.createCollection('products')` <br><br>
заполснение коллекции данными  <br>
`db.products.insertMany([ 
{name: "Комп", model : "intel1", price: 16 }, 
{name: "Комп", model : "intel2", price: 161 },
{name: "Комп", model : "intel4", price: 168 },
{name: "Комп", model : "intel4", price: 14 },
{name: "Комп", model : "intel5", price: 16 },
{name: "Комп", model : "md4", price: 10000 },
{name: "Комп", model : "ls2", price: 2100 },
{name: "Ноут", model : "15inc", price: 161 },
{name: "Комп", model : "16inc", price: 516 },
{name: "Комп", model : "18inc", price: 33 },
{name: "Ручка", model : "дверная", price: 1.66 },
{name: "Ручка", model : "дверная1", price: 1.68 },
{name: "Ручка", model : "дверная2", price: 1.69 },
{name: "Мяч", model : "синий", price: 1 },
{name: "мяч", model : "желтый", price: 0.16 },
{name: "стол", model : "intel15", price: 888 },
{name: "стул", model : "intel18", price: 777 },
{name: "лампа", model : "lampmodel", price: 16 },
{name: "мышь", model : "intel1", price: 0.16 },
{name: "наушники", model : "intel1", price: 1.67 }
]
)`  <br>

запросы на поиск <br>
`db.products.find({"name": "лампа"})` <br>
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa7c"), "name" : "лампа", "model" : "lampmodel", "price" : 16 } <br>

`db.products.find({"price": {$lt : 10}})` <br>

{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa75"), "name" : "Ручка", "model" : "дверная", "price" : 1.66 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa76"), "name" : "Ручка", "model" : "дверная1", "price" : 1.68 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa77"), "name" : "Ручка", "model" : "дверная2", "price" : 1.69 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa78"), "name" : "Мяч", "model" : "синий", "price" : 1 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa79"), "name" : "мяч", "model" : "желтый", "price" : 0.16 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa7d"), "name" : "мышь", "model" : "intel1", "price" : 0.16 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa7e"), "name" : "наушники", "model" : "intel1", "price" : 1.67 } <br>

`db.products.find({"name": {$in: ["мяч", "Ручка"]}})` <br>

{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa75"), "name" : "Ручка", "model" : "дверная", "price" : 1.66 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa76"), "name" : "Ручка", "model" : "дверная1", "price" : 1.68 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa77"), "name" : "Ручка", "model" : "дверная2", "price" : 1.69 }
{ "_id" : ObjectId("6280af001dbb7eb5cdd7aa79"), "name" : "мяч", "model" : "желтый", "price" : 0.16 } <br>

запрос на обновлние <br>
`db.products.update({"name" : "Ручка"}, {$set: {"model" : "разные"}} , {multi : true})` <br>

WriteResult({ "nMatched" : 3, "nUpserted" : 0, "nModified" : 3 }) <br>
}






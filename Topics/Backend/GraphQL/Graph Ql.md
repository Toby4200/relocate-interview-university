
Graph ql - это технология, которая разработана и поддерживается facebook
Это прослойка между базой данных и front-end, которая абстрагируе реализацию и базу данных
Позволяет запросить с бека только то, что нужно и скомбинировать это все в один запрос
На этом уровне нет бизнес логики

**Ее основные преимущества**
- Она работает с плохим соединением - даже на слабом интернете
- Нужно делать меньше запросов, чем с REST
- Можно двигаться быстрее - тк нужно меньше тратить времени на доработку
- Проще разбираться с бэком
- Есть валидация запросов перед выполнением кода


**Проблемы REST api**
- n + 1 проблема


# Курсы

1. [[Язык запросов graphQL]] | ENG | [link](https://coursehunter.net/course/yazyk-zaprosov-graphql?lesson=1)
2. [[howtographql - официальный курс]] | ENG | [link](https://www.howtographql.com/basics)

## Сущности graphQl

- mutations: insert, update, delete
- query

**graphql состоит из 2 физических составляющих**
- серверный рантайм
- язык запросов, который вызывается с front-end



### безопасен ли graphql?



https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types


# Union Types

Ts позволяет обьеденять несколько типов
Это может приводить к проблеме, что некоторые методы могут не существовать на разных типах

```ts
function printId(id: number | string) {
  if (typeof id === "string") {
    // In this branch, id is of type 'string'
    console.log(id.toUpperCase());
  } else {
    // Here, id is of type 'number'
    console.log(id);
  }
}
```

Для решения этой проблемы может быть полезен оператор `typeof` или метод `isArray` у массива


### Вот интересное упражнение на эту тему

https://typescript-exercises.github.io/#exercise=2&file=%2Findex.ts

```ts
/*

Intro:

    All 2 users liked the idea of the community. We should go
    forward and introduce some order. We are in Germany after all.
    Let's add a couple of admins.

    Initially, we only had users in the in-memory database. After
    introducing Admins, we need to fix the types so that
    everything works well together.

Exercise:

    Type "Person" is missing, please define it and use
    it in persons array and logPerson function in order to fix
    all the TS errors.

*/
interface User {
  name: string;
  age: number;
  occupation: string;
}

interface Admin {
  name: string;
  age: number;
  role: string;
}

export type Person = User | Admin;

export const persons: Person[] = [
  {
      name: 'Max Mustermann',
      age: 25,
      occupation: 'Chimney sweep'
  },
  {
      name: 'Jane Doe',
      age: 32,
      role: 'Administrator'
  },
  {
      name: 'Kate Müller',
      age: 23,
      occupation: 'Astronaut'
  },
  {
      name: 'Bruce Willis',
      age: 64,
      role: 'World saver'
  }
];

export function logPerson(user: Person) {
  console.log(` - ${user.name}, ${user.age}`);
}

persons.forEach(logPerson);

// In case you are stuck:
// https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types
```


Суть упражнения в том, чтобы понять как обьеденять 2 типа, чтобы они могли иметь разные поля в одном обьекте
В данном случае могут приходить разные значения для обычного пользователя и админа
Это очень наглядное разделение сущностей даже если между ними есть похожие поля - очень хорошее решение с точки зрения команды, которая делает ts.

# Interfaces

- [ ] Хорошее обьяснение разницы типов и интерфейсов


---
tags:
  - react
  - hooks
Tutorial link:
  - https://react.dev/learn/synchronizing-with-effects
  - https://react.dev/reference/react/useEffect
link1: https://react.dev/learn/you-might-not-need-an-effect | Caching expensive calculations ✅
---
# В этой теме есть ответы на следующие вопросы
- Что такое хуки и как их использовать?
- 

# Что это

useEffect - это хук

useEffect позволяет синхронизировать состояние динамических элементов: state, props, переменных в функциональных компонентах с любыми другими системами

Позволяет синхронизироваться с внешними системам
- Менять state
- Делать запросы - например fetch или axios
- Отсылать аналитику при отображении
- Устанавливать коннектс сервером

# Какой функционал он заменяет в class-based подходе

Хук useEffect имеет следующее API

```tsx
useEffect(setup, dependencies?)
```

Он подменяет функционал 3 жизненных методов в React.js до версии 16.8

## **componentDidUpdate** - отрабатывает 1 раз при первом рендере компонента

- If the dependency array is empty, then the `useEffect` will only run once, after the first paint.

```tsx
useEffect(() => {
    // Your code here
}, []); // The empty array causes this effect to run only once after initial render.
```

## **componentWillUnmount** - этот lifecicle method выполняется перед тем как компонент будет уничтожен

Он напоминает отписку у таймера setTimeout или отписку от события в js

This function can return another function called the clean-up function, which can be used to clean up the side effects (i.e. when the component is destroyed) like unsubscribing to a store.

С useEffect отписка перед уничтожением компонента будет выглядеть так

```tsx
useEffect(() => {
    // Your code here

   return () => {
       // Cleanup code goes here - runs just before component unmounts.
   }
}, []);
```


## Когда useEffect не нужен?

Этот хук применяется для соеденения с внешними системами
- сеть
- dom - дерево
- внешний виджет

Его не стоит использовать для обновления state - иначе произойдет 2 ререндера компонента, вместо 1


```tsx
function Form() {  

const [firstName, setFirstName] = useState('Taylor');  

const [lastName, setLastName] = useState('Swift');  

// ✅ Good: calculated during rendering  

const fullName = firstName + ' ' + lastName;  

// ...  

}
```
Тк функция выполняется каждый раз - то можно не создавать лишний стейт и не использовать хук, тк компонент будет пересчитан при любом изменении state или props





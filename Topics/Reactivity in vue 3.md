
Реактивность поменялась при обновлении на 3 vue
Теперь предпочитаемый способ - это создание свойств через ref

# `ref`

ref - это обьект со значением value
При использовании делает переданное значение реактивным и записывает ссылку на него в переменную

### Пример как создавать ref и менять

```ts
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)

    function increment() {
      // .value is needed in JavaScript
      count.value++
    }

    // don't forget to expose the function as well.
    return {
      count,
      increment
    }
  }
}
```

При использовании ref в шаблоне писать .value не нужно - происходит автоматическое развертывание

```ts
<button @click="increment">
  {{ count }}
</button>
```


# `<script setup>`


Если указать аттрибут `setup` - тогда все, что будет обьявлено на первом уровне будет доступно в шаблоне

```ts
<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

<template>
  <button @click="increment">
    {{ count }}
  </button>
</template>
```


Все, что определено в `script` - становится доступно в `template`
Можно воспринимать `template` как функцию на том же уровне, которой доступны все переменные `script`

# Почему refs?

Система реактивности vue делает несколько вещей

- Запоминает каждый ref
- Запускает ререндер, когда ref меняется

Переменные в js не умеют отслеживать изменение значений
И для этого создан ref тк обьекты имеют get и set методы, которые позволяют вмешиваться и добавлять логику при изменении значения

Ниже псевдокод того, как работют ref 

```ts
// pseudo code, not actual implementation
const myRef = {
  _value: 0,
  get value() {
    track()
    return this._value
  },
  set value(newValue) {
    this._value = newValue
    trigger()
  }
}
```

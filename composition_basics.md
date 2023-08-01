# Composition API

Composition API is a new addition to VueJS 3.

It works different than the options API where we have to declare everything (methods, computed...) in the body setup(){} within the script tag.

The variables we declare are not directly available in the template tag. We have to declare them in the return body so they can be available.

### Reactivity

The reactivity is also different.Variables are not reactives right away. We have to declare the reactive variables explicitly. We use a decoupled reactivity where we have to import and define what should be reactive.

For most part, the template works the same as in the Options API.

v-model doesn't work as usually in the options API.

To make use of reactivity, we have to import the reactive reference system. Vue offers two reactive systems: ref and reactive.
After import, we declare our reactive variables.

#### Ref

```js
import { ref } from 'vue'

const msg = ref('Hello World') // this makes msg reactive and works with v-model
```

ref() is used with a primitive value mostly [might take as well an object] and returns an object. This means our variable (msg) is an object. To access its value, we use the notation object.value.

```js
import { ref } from 'vue'

const msg = ref('Hello World') // this makes msg reactive and works with v-model
console.log(msg.value)
```

To access our reactive value in the template, we don't have to use the object.value notation since Vue assumes we mostly render those reactive variables in our template and handle that process in the background for us. This is called ref unwrapping.

```js
import { ref } from 'vue'

const msg = ref('Hello World') // this makes msg reactive and works with v-model
console.log(msg.value)

//{{ msg }} => In the background, {{ msg.value }}
<template>
    <p>{{ msg }}</p>
<template>
```

#### Reactive

reactive is another way to achieve reactivity with the composition API. In contrast to ref, it takes in a complex (non primitive) data such as object as the parameter.

With reactive, we don't need to use the object.value notation to get the value of our reactive data.

```js
import { reactive } from 'vue'

const numbers = reactive({
    one: 0,
    two: 0
}) // this makes msg reactive and works with v-model

//{{ msg }} => In the background, {{ msg.value }}
<template>
    <p>{{ numbers.one }}</p>
    <p>{{ numbers['two'] }}</p>
<template>
```

reactive is similar to data() in the options API.

### Methods

We declare methods as in plain JS using the function definition or the ES6+ syntax (arrow function) since our methods our not in an object as in the options API.

```js
import { ref } from 'vue'

const msg = ref('Hello World') // this makes msg reactive and works with v-model

function hello(){
 // definition here
}

const hi = () => {
    // definition here
} 
```

### Computed properties

In order to create computed properties, we have to import the computed reference from vue and wrap it around the function we'd like to use as a computed property.

```js
import { ref, computed } from 'vue'

const price = ref(0)

const qty = ref(0)

const total = computed({
    return price.value * qty.value
})
```

### watch and watchEffect

watch and watchEffect are two ways to listen to our data for change and when any occurs, to trigger some actions.

There are some differences. In watch, we have to specify what we want to listen to (observe) and we must specify as an option if we want immediate action. With watchEffect, we don't have to specify anything to watch for, we can pass in whatever we like.

watch is seen as more specific while watchEffect is seen as more general.

```js
import { watch, watchEffect} from 'vue'

const price = ref(0)

const qty = ref(0)

watch(price, (newVal) => {
    console.log(`Price value has changed to ${newVal}`)
})

watchEffect(() => {
    console.log(`Quantity has changed to ${qty}`)
})
```

watch (watchEffect) is useful when we want to watch for change in dynamic data and maybe fetch, render data based on those changes. As an example, we can think of an :id parameter in an url (/user/:id)
# Composition API

Composition API is a new addition to VueJS 3.

It works different than the options API where we have to declare everything (methods, computed...) in the body setup(){} within the script tag.

The variables we declare are not directly available in the template tag. We have to declare them in the return body so they can be available.

### Reactivity

The reactivity is also different.Variables are not reactives right away. We have to declare the reactive variables explicitly. We use a decoupled reactivity where we have to import and define what should be reactive.

For most part, the template works the same as in the Options API.

v-model doesn't work as usually in the options API.

To make use of reactivity, we have to import the reactive reference system (ref) and declare our reactive variables.

```js
import { ref } from 'vue'

const msg = ref('Hello World') // this makes msg reactive and works with v-model
```
<script setup>
import { ref, reactive } from 'vue'
//import HelloWorld from './components/HelloWorld.vue'



const count = ref(0)

const numbers = reactive({
  a: 0,
  b: 0
})

const increment = () => {
  count.value++
}

const increase = (num) => {
  numbers[num]++
}

</script>

<template>
  <main>
    <button @click="increment">{{ count }}</button>
    <button @click="increase('a')">{{ numbers.a }}</button>
    <button @click="increase('b')">{{ numbers.b }}</button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

button {
  height: 100px;
  width: 100px;
  font-size: 20px;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

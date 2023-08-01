<script setup>
import { ref } from 'vue'
//import HelloWorld from './components/HelloWorld.vue'



const count = ref(0)

const increment = () => {
  count.value++
}

</script>

<template>
  <main>
    <button @click="increment">{{ count }}</button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

button {
  height: 200px;
  width: 200px;
  font-size: 40px;
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

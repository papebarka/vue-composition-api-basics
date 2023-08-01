<script setup>
import { ref, reactive, computed } from 'vue'
//import HelloWorld from './components/HelloWorld.vue'



const count = ref(0)

const numbers = reactive({
  one: 0,
  two: 0
})

const increment = () => {
  count.value++
}

const increase = (num) => {
  numbers[num]++
}

watch(count, (newVal) => {
  console.log(newVal)
})

const total = computed(() => {
  return count.value + numbers.one + numbers.two
}, {
  immediate: true
})

</script>

<template>
  <main>
    <button @click="increment">{{ count }}</button>
    <button @click="increase('one')">{{ numbers.one }}</button>
    <button @click="increase('two')">{{ numbers.two }}</button>

    <p class="total">
      Total is: {{ total }}
    </p>
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

.total {
  padding: 25px;
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

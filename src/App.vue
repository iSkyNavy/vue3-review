<script setup>
import { ref } from 'vue';

  console.log('vueeee');
  const author = "Diego Ramos";
  const fruits= ["fresa", "lucuna", "mango"];
  const count = ref(0);
  const favoriteNumbers = ref([]);;


  const handleIncrement = () => {
    count.value++;
  }
  const handleDecrement = () => {
    count.value--;
  }
  const handleAddNumber = () => {
    favoriteNumbers.value.push(count.value);
  }
</script>

<template>
  <h1>Hola Mundo {{author}}</h1>

  <ul>
    <li v-for="(fruit, index) in fruits" :key="index">{{ fruit }}</li>
  </ul>
  <h2 :style="'color:' + `${count <= 0 ? 'red' : 'green'};`">{{ count }}</h2>
  <h3>{{ favoriteNumbers }}</h3>
  <button @click="handleIncrement">Increment</button>
  <button @click="handleDecrement">Decrement</button>
  <button @click="count=0">Reset</button>
  <button @click="handleAddNumber" :disabled="favoriteNumbers.includes(count)">Add</button>

</template>

<style>
  h1 {
    color: blue;
  }
</style>
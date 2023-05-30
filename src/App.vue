<script setup>
  import { ref, onMounted } from 'vue';
  import { useCounterStore } from '@/stores/counter'
  import Products from './components/Products.vue';

  import axios from 'axios';

  const counter = useCounterStore()
  console.log('這個是組件用 pinia', counter.count)
  const products = ref([]);

  const getData = async () => {
    const response = await axios.get('https://fakestoreapi.com/products');
    products.value = response.data;
    console.log('我是組件裡的 getData', response.data)
  };

  onMounted(getData);
</script>

<template>
  <main>
    <h1 class="text-base">Im Test!!!</h1>
    <Products :products="products" />
  </main>
</template>

<style scoped>
</style>
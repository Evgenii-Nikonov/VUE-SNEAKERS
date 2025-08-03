<script setup>
import { ref } from 'vue'
const props = defineProps({
  title: String,
  price: Number,
  isAdded: Boolean,
})
</script>

<template>
  <div class="product">
    <h1>Товар: {{ title }}</h1>
    <h2>цена: {{ price }}</h2>
    <h3>Добавлен: {{ isAdded }}</h3>

    <slot></slot>
  </div>
</template>

<style scoped>
.product {
  border: 1px solid teal;
  padding: 12px;
  /* margin-bottom: 10px; */
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: center;
  width: 20%;
}
</style>

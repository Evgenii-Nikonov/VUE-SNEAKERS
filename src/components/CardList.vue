<script setup>
import Card from './Card.vue'
defineProps({
  items: Array,
})

let isAdded = false
let isFavorite = false

const onClickAdd = () => {
  isAdded = !isAdded
}
const onClickFavorite = () => {
  isFavorite = !isFavorite
}
</script>

<template>
  <div class="cards grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :isAdded="isAdded"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>

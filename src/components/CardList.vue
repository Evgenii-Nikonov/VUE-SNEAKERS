<script setup>
import { ref } from 'vue'
import Card from './Card.vue'
ref
defineProps({
  items: Array,
})

let isAdded = ref(false)
let isFavorite = ref(false)

const onClickAdd = () => {
  isAdded.value = !isAdded.value
}
const onClickFavorite = () => {
  isFavorite.value = !isFavorite.value
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
      :isFavorite="isFavorite"
      :onClickAdd="onClickAdd"
      :onClickFavorite="onClickFavorite"
    />
  </div>
</template>

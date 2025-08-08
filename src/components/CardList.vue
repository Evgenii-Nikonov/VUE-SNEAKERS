<script setup>
import Card from './Card.vue'

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
      imageUrl="/sneakers/sneakers-1.jpg"
      title="Мужские кросовки Nike Blazer mid"
      :price="5000"
      :isAdded="isAdded"
      :onClickAdd="onClickAdd"
    />
    <Card />
  </div>
</template>

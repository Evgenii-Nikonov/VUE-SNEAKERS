<script setup>
import { ref, inject } from 'vue'
import Card from './Card.vue'

defineProps({
  items: Array,
})

const addToFavorite = inject('addToFavorite')
</script>

<template>
  <div class="cards grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :id="item.id"
      :key="item.id"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :isFavorite="item.isFavorite"
      :onClickFavorite="() => addToFavorite(item)"
    />
  </div>
</template>

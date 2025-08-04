<script setup>
import Card from './Card.vue'

const props = defineProps()
</script>

<template>
  <div class="cards grid grid-cols-4 gap-5">
    <Card
      imageUrl="/sneakers/sneakers-1.jpg"
      title="Мужские кросовки Nike Blazer mid"
      :price="5000"
    />
    <Card />
  </div>
</template>

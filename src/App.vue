<script setup>
import MyComponent from './components/MyComponent.vue'
</script>

<template>
  <div class="text-3x1 font-bold underline bg-green">
    <MyComponent title="adidas must only" :price="14999" :isAdded="false" />
  </div>
</template>

<style scoped></style>

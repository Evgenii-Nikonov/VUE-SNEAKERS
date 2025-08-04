<script setup>
defineProps({
  imageUrl: String,
  title: String,
  price: Number,
})
</script>

<template>
  <div
    class="bg-white relative border border-slate-300 rounded-3xl p-8 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition"
  >
    <img src="/like-2.svg" alt="like" class="absolute top-8 left-8" />
    <img :src="imageUrl" alt="sneaker" />
    <p class="mt-2">{{ title }}</p>

    <div class="flex justify-betwee mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400">Цена:</span>
        <b>{{ price }} руб.</b>
      </div>
      <img src="/plus.svg" alt="plus" />
    </div>
  </div>
</template>

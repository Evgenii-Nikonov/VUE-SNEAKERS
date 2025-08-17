<script setup>
import { ref } from 'vue'

defineProps({
  imageUrl: String,
  title: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function,
})

let isFavorit = ref(false)

const changeFavorite = () => {
  isFavorit.value = !isFavorit.value
}
</script>

<template>
  <div
    class="bg-white relative border border-slate-300 rounded-3xl p-8 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition"
  >
    <img
      @click="changeFavorite"
      :src="!isFavorit ? '/like-2.svg' : '/like-1.svg'"
      alt="like"
      class="absolute top-8 left-8"
    />
    <img :src="imageUrl" alt="sneaker" />
    <p class="mt-2">{{ title }}</p>

    <div class="flex justify-betwee items-end mt-5">
      <div class="flex flex-col flex-1">
        <span class="text-slate-400">Цена:</span>
        <b>{{ price }} руб.</b>
      </div>
      <img @click="onClickAdd" :src="isAdded ? '/plus.svg' : '/checked.svg'" alt="plus" />
    </div>
  </div>
</template>

<script setup>
import { inject } from 'vue'

const emit = defineEmits(['onClickRemove'])

defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number,
})

const { addToCart } = inject('cart')
</script>

<template>
  <div class="flex flex-items-center border border-slate-100 p-4 rounded-xl gap-4 mb-5">
    <img class="w-16 h-16" :src="imageUrl" alt="sneaker" />
    <div class="flex flex-col">
      <p>{{ title }}</p>
      <div class="flex justify-between mt-2">
        <b>{{ price }} руб. </b>
        <img
          @click="emit('onClickRemove')"
          class="opacity-40 hover:opacity-100 transition cursor-pointer"
          src="/close.svg"
          alt="close icon"
        />
      </div>
    </div>
  </div>
</template>

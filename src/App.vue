<script setup>
import { onMounted, ref } from 'vue'

import axios from 'axios'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'

const items = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get('https://0d2e8a6fb9e1c979.mokky.dev/items')
    items.value = data
  } catch (err) {
    console.log(err)
  }
})
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-15">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <div class="flex gap-4">
          <select vlass="border [y-2 px-3 rounded-md outline-none cursor-pointer" name="" id="">
            <option value="">По названию</option>
            <option value="">По цене (дешёвые)</option>
            <option value="">По цене (дорогие)</option>
          </select>
        </div>

        <div class="relative">
          <img class="absolute left-4 top-3" src="/search.svg" alt="" />
          <input
            class="border rounded-md py-2 pl-12 pr-4 outline-none focus:border-gray-400"
            type="text"
            placeholder="Поиск..."
          />
        </div>
      </div>

      <CardList :items="items" />
    </div>
  </div>
</template>

<style scoped></style>

<script setup>
import MyComponent from './components/MyComponent.vue'
</script>

<template>
  <div class="bg-white w-4/5 m-auto h-screen rounded-xl shadow-xl mt-15">
    <header class="flex justify-between border-b border-slate-300 px-10 py-8">
      <div class="flex items-center gap-4">
        <img class="w-10" src="/logo.png" alt="" />
        <div class="">
          <h1 class="text-xl font-bold uppercase">vue sneakers</h1>
          <p class="text-slate-400">Магазин лучших кросовок</p>
        </div>
      </div>

      <ul class="flex items-center gap-10 text-gray-500">
        <li class="flex items-center gap-3 hover:text-black cursor-pointer duration-150 ease-in">
          <img src="/cart.svg" alt="" />
          <span class="font-bold">1205 руб.</span>
        </li>
        <li class="flex items-center gap-3 hover:text-black cursor-pointer duration-150 ease-in">
          <img src="/heart.svg" alt="" />
          <span>Закладки</span>
        </li>
        <li class="flex items-center gap-3 hover:text-black cursor-pointer duration-150 ease-in">
          <img src="/profile.svg" alt="" />
          <span>Профиль</span>
        </li>
      </ul>
    </header>
  </div>
</template>

<style scoped></style>

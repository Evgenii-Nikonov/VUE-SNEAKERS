<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'

defineProps({
  hideDrawer: Function,
})
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-50"></div>
  <div class="flex flex-col bg-white w-100 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead :hideDrawer="hideDrawer" />
    <CartItemList />

    <div class="flex flex-col gap-4 mb-5 my-7">
      <div class="flex gap-2">
        <span>Итого:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>12900 ₽</b>
      </div>
      <div class="flex gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>900 ₽</b>
      </div>

      <button
        class="mt-4 bg-lime-500 rounded-xl w-full py-3 disabled:bg-slate-300 disabled:cursor-none text-white hover:bg-lime-600 transition active:bg-lime-700 cursor-pointer"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>

<style></style>

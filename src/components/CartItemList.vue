<script setup>
import { inject } from 'vue'
import CartItem from './CartItem.vue'

const { cartItems, removeFromCart } = inject('cart')

const onClickRemove = () => {
  addToCart(item)
}
</script>

<template>
  <div class="flex flex-col flex-1">
    <CartItem
      v-for="item in cartItems"
      :key="item.id"
      :id="item.id"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      @on-click-remove="removeFromCart(item)"
    />
  </div>
</template>

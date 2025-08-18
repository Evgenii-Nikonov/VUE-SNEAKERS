<script setup>
import { watch, computed, onMounted, ref, reactive, provide } from 'vue'

import axios from 'axios'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'

let isShowDrawer = ref(false)

// Состояние (state) которое хранит все кросовки полученные с сервера
const items = ref([])
// const favoritesItems = ref([])

// Реактивные стейт для фильтров
const filters = reactive({
  sortBy: 'title',
  searchQuery: '',
})
// Функция запроса на сервер при изменении фильтров либо при монтировании компонента
const fetchItems = async () => {
  try {
    let params = {
      sortBy: filters.sortBy,
    }

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get(`https://0d2e8a6fb9e1c979.mokky.dev/items`, { params })
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      isAdded: false,
    }))
  } catch (err) {
    console.log(err)
  }
}

const fetchFavorites = async () => {
  try {
    const { data: favorites } = await axios.get(`https://0d2e8a6fb9e1c979.mokky.dev/favorites`)
    items.value = items.value.map((item) => {
      const favorite = favorites.find((fav) => fav.parentId === item.id)
      if (!favorite) {
        return item
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      }
    })
  } catch (err) {
    console.log(err)
  }
}

// Реализация поиска по товарам на стороне фронтенда, пока оставить

// const filteredItems = computed(() => {
//   return items.value.filter(
//     (item) => item.title && item.title.toLowerCase().includes(searchQuery.value.toLowerCase()),
//   )
// })

const showDrawer = () => {
  isShowDrawer.value = true
}

const hideDrawer = () => {
  isShowDrawer.value = false
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})

//*При изменении sortby делается запрос к серверу в который будет передаваться 'sortby' + sortby
watch(filters, fetchItems)

const addToFavorite = async (item) => {
  try {
    if (!item.isFavorite) {
      const obj = { parentId: item.id }

      item.isFavorite = true
      const { data } = await axios.post(`https://0d2e8a6fb9e1c979.mokky.dev/favorites`, obj)

      item.favoriteId = data.id

      console.log(data)
    } else {
      item.isFavorite = false
      const { data } = await axios.delete(
        `https://0d2e8a6fb9e1c979.mokky.dev/favorites/${item.favoriteId}`,
      )

      item.favoriteId = null
    }
  } catch (err) {
    console.log(err)
  }
}
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-15">
    <Header :onClickDrawer="showDrawer" />
    <Drawer :hideDrawer="hideDrawer" v-if="isShowDrawer" />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <div class="flex gap-4">
          <select
            v-model="filters.sortBy"
            class="border border-gray-300 py-2 px-3 rounded-md outline-none cursor-pointer transition"
            name=""
            id=""
          >
            <option value="name">По названию</option>
            <option value="price">По цене (дешёвые)</option>
            <option value="-price">По цене (дорогие)</option>
          </select>
        </div>

        <div class="relative">
          <img class="absolute left-4 top-3" src="/search.svg" alt="" />
          <input
            v-model="filters.searchQuery"
            class="border border-gray-300 rounded-md py-2 pl-12 pr-4 outline-none focus:border-gray-500"
            type="text"
            placeholder="Поиск..."
          />
        </div>
      </div>

      <CardList :items="items" @addToFavorite="addToFavorite" />
    </div>
  </div>
</template>

<style scoped></style>

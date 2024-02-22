<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'
import PaginationMenu from './components/PaginationMenu.vue'
import ProductCard from './components/ProductCard.vue'

let count = ref(0)
let itemsOnPage = 6
let pages = ref([])
let recipes = ref([])
let currentRecipes = ref([])
let currPage = ref(1)
onMounted(async () => {
  let res = await axios.get('https://dummyjson.com/recipes')
  res = res.data.recipes
  recipes.value = res
  count.value = res.length
  pages.value = Array(Math.ceil(count.value / itemsOnPage))
  changePage(1)
})

function changePageNumber(pageNum) {
  currPage.value = pageNum
  changePage(pageNum)
}

function changePage(pageNum) {
  currentRecipes.value = recipes.value.slice((pageNum - 1) * itemsOnPage, pageNum * itemsOnPage)
}
</script>

<template>
  <div class="container">
    <h1>Recipes</h1>
    <pagination-menu
      @change-page="changePageNumber"
      :max-page="Math.ceil(count / itemsOnPage)"
      :buttons="pages"
      :curr-page="currPage"
    ></pagination-menu>
    <product-card :recipes="currentRecipes"></product-card>
  </div>
</template>

<style scoped>
h1 {
  font-size: 48px;
  font-weight: 400;
  margin-top: 35px;
  margin-bottom: 52px;
}

.container {
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>

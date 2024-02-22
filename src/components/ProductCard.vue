<template>
  <div class="cards">
    <div class="card" v-for="recipe in recipes" :key="recipe.id">
      <img class="img" :src="recipe.image" alt="" />
      <h2 class="card_header">{{ recipe.name }}</h2>
      <p class="card_text">Difficulty: {{ recipe.difficulty }}</p>
      <p class="card_text">Cuisine: {{ recipe.cuisine }}</p>
      <p class="card_text">Calories per Serving: {{ recipe.caloriesPerServing }}</p>
      <h2 class="card_header">Ingridients:</h2>
      <ul class="ingridients">
        <li class="card_text" v-for="(ingredient, ix) in recipe.ingredients" :key="ix">
          {{ ingredient }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script setup>
defineProps({ recipes: Array })
</script>
<style scoped>
.cards {
  display: grid;
  grid-template-columns: repeat(3, 224px);
  column-gap: 75px;
  row-gap: 58px;
}
.img {
  width: 100%;
  height: auto;
}

.card {
  border: 1px solid #e4e4e4;
  width: fit-content;
  margin-bottom: 20px;
  width: 224px;
  overflow: hidden;
  border-radius: 25px;
  box-shadow: 0px 4px 4px 0px #00000040;
}

.card_text {
  font-size: 12px;
  font-weight: 400;
  line-height: 15px;
  margin-bottom: 5px;
  margin-left: 12px;
}

.card_header {
  font-size: 16px;
  font-weight: 700;
  line-height: 20px;
  margin-bottom: 5px;
  margin-left: 12px;
  margin-top: 15px;
}

.ingridients {
  margin-left: 18px;
  margin-bottom: 32px;
}
</style>

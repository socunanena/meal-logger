<template>
  <div>
    <meal-input v-on:add-meal="addMeal"/>
    <nuxt/>
  </div>
</template>

<script>
  import MealInput from '~/components/meal-input/index.vue';

  export default {
    components: {
      MealInput,
    },
    data: () => ({
      meals: [],
    }),
    methods: {
      addMeal(meal) {
        this.meals.push(meal);
      },
    },
  }
</script>

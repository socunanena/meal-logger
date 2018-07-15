<template>
  <div>
    <meal-input v-on:add-meal="addMeal" />
  </div>
</template>

<script>
  import MealInput from './components/meal-input/index';

  export default {
    name: 'Calendar',
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
  };
</script>

<style scoped>
</style>

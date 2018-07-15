<template>
  <div>
    <meal-input v-on:add-meal="addMeal"/>
    <day-view :meals="meals"/>
  </div>
</template>

<script>
  import MealInput from './components/meal-input/index';
  import DayView from './components/day-view/index';

  export default {
    name: 'Calendar',
    components: {
      MealInput,
      DayView,
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

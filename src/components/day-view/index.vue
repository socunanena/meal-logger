<template>
  <div>
    <ul>
      <li v-for="meal in mealsOfTheDay">
        <strong>{{ formatDate(meal.date, 'YYYY-MM-DD HH:mm') }}:</strong>
        {{ meal.content }}
      </li>
    </ul>
  </div>
</template>

<script>
  import fecha from 'fecha';

  export default {
    name: 'DayView',
    props: ['meals'],
    data() {
      return {
        day: new Date().getDate(),
      }
    },
    computed: {
      mealsOfTheDay() {
        return this.meals
          .filter(meal => meal.date.getDate() === this.day)
          .sort((mealA, mealB) => mealA.date - mealB.date);
      },
    },
    methods: {
      formatDate: fecha.format,
    },
  };
</script>

<style scoped>
</style>

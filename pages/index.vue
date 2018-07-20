<template>
  <ul>
    <li v-for="meal in mealsOfTheDay">
      <strong>{{ meal.date }} -</strong>
      {{ meal.content }}
    </li>
  </ul>
</template>

<script>
  import fecha from 'fecha';

  export default {
    head: {
      title: 'Meals'
    },
    asyncData() {
      const mealsOfTheDay = [
        { date: new Date(2018, 7, 27, 10, 30), content: 'esmorzar' },
        { date: new Date(2018, 7, 27, 13, 30), content: 'dinar' },
        { date: new Date(2018, 7, 27, 20, 30), content: 'sopar' },
      ];

      return {
        mealsOfTheDay: mealsOfTheDay.map(m => ({ ...m, date: fecha.format(m.date, 'YYYY-MM-DD HH:mm')}))
      };
    },
  };
</script>

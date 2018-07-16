<template>
  <div>
    <div>
      <date-picker
              type="date"
              format="YYYY-MM-DD"
              :lang="timePickerOptions.lang"
              first-day-of-week.number=1
              v-model="day"
      />
    </div>
    <ul>
      <li v-for="meal in mealsOfTheDay">
        <strong>{{ formatDate(meal.date, 'YYYY-MM-DD HH:mm') }} -</strong>
        {{ meal.content }}
      </li>
    </ul>
  </div>
</template>

<script>
  import fecha from 'fecha';
  import DatePicker from 'vue2-datepicker';

  export default {
    name: 'DayView',
    components: { DatePicker },
    props: ['meals'],
    data() {
      return {
        day: new Date(),
        timePickerOptions: {
          lang: {
            days: ['Dl', 'Dt', 'Dc', 'Dj', 'Dv', 'Ds', 'Dg'],
            months: ['Gener', 'Febrer', 'Març', 'Abril', 'Maig', 'Juny', 'Juliol', 'Agost', 'Setembre', 'Octubre', 'Novembre', 'Desembre'],
            placeholder: {
              date: 'Seleccioneu una data',
            },
          },
        },
      }
    },
    computed: {
      mealsOfTheDay() {
        return this.meals
          .filter(meal => fecha.format(meal.date, 'YY-M-D') === fecha.format(this.day, 'YY-M-D'))
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

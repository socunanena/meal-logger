<template>
  <div>
    <div>
      <no-ssr>
        <date-picker
                type="date"
                format="YYYY-MM-DD"
                :lang="timePickerOptions.lang"
                first-day-of-week.number=1
                v-model="day"
        />
      </no-ssr>
    </div>
  </div>
</template>

<script>
  import fecha from 'fecha';

  export default {
    name: 'DayView',
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

<template>
  <div>
    <form v-on:submit.prevent="createMeal">
      <no-ssr>
        <date-picker
                type="datetime"
                format="YYYY-MM-DD HH:mm"
                :lang="timePickerOptions.lang"
                first-day-of-week.number=1
                :time-picker-options="timePickerOptions.timeSteps"
                v-model="date"
        />
      </no-ssr>
      <input title="Content" v-model="content"/>
      <input type="submit" value="Afegir àpat" title="Afegir àpat"/>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'MealInput',
    data: () => ({
      date: new Date(),
      content: undefined,
      timePickerOptions: {
        lang: {
          days: ['Dl', 'Dt', 'Dc', 'Dj', 'Dv', 'Ds', 'Dg'],
          months: ['Gener', 'Febrer', 'Març', 'Abril', 'Maig', 'Juny', 'Juliol', 'Agost', 'Setembre', 'Octubre', 'Novembre', 'Desembre'],
          placeholder: {
            date: 'Seleccioneu una data',
          },
        },
        timeSteps: { start: '00:00', step: '00:30', end: '23:30' },
      },
    }),
    methods: {
      createMeal() {
        if (this.content) {
          this.$emit('add-meal', { date: this.date, content: this.content });

          this.content = undefined;
        }
      },
    },
  };
</script>

<style scoped>
</style>

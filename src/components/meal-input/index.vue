<template>
  <div>
    <form v-on:submit.prevent="$emit('add-meal', { date, content })">
      <date-picker
        type="datetime"
        format="YYYY-MM-DD HH:mm"
        :lang="timePickerOptions.lang"
        first-day-of-week.number=1
        :time-picker-options="timePickerOptions.timeSteps"
        v-model="date"
      />
      <input title="Content" v-model="content" />
      <button type="submit" title="go!" />
    </form>
  </div>
</template>

<script>
  import DatePicker from 'vue2-datepicker';

  export default {
    name: 'MealInput',
    components: {
      DatePicker,
    },
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
  };
</script>

<style scoped>
</style>

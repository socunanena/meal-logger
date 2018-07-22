<template>
  <no-ssr>
    <full-calendar :events="mealsOfTheDay" :config="config"/>
  </no-ssr>
</template>

<script>
  import fecha from 'fecha';
  import axios from 'axios';
  // import 'fullcalendar/dist/locale/ca';

  export default {
    head: {
      title: 'Meals',
    },
    data() {
      return {
        config: {
          header: {
            left: 'today',
            center: 'prev title next',
            right: 'agendaWeek,agendaDay',
          },
          buttonText: {
            prev: '<',
            next: '>',
          },
          titleFormat: 'YYYY-MM-DD',
          allDaySlot: false,
          minTime: '07:00',
          maxTime: '22:00',
          firstDay: 1,
          columnHeaderFormat: 'dddd',
          slotLabelFormat: 'HH:mm',
          themeSystem: 'bootstrap4',
        },
      };
    },
    async asyncData() {
      const { data: { meals } } = await axios.get('http://localhost:3001/api/meals');

      return {
        mealsOfTheDay: meals.map(m => ({
          start: m.date,
          title: m.content,
        })),
      };
    },
  };
</script>

<style>
  @import '../node_modules/fullcalendar/dist/fullcalendar.css';
  @import 'https://bootswatch.com/4/cerulean/bootstrap.min.css'; /* https://fullcalendar.io/releases/fullcalendar/3.9.0/demos/themes.html */
</style>

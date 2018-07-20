<template>
  <no-ssr>
    <full-calendar :events="mealsOfTheDay" :config="config"/>
  </no-ssr>
</template>

<script>
  import fecha from 'fecha';
  // import 'fullcalendar/dist/locale/ca';

  export default {
    head: {
      title: 'Meals',
    },
    asyncData() {
      const mealsOfTheDay = [
        { date: new Date(2018, 6, 20, 10, 30), content: 'esmorzar' },
        { date: new Date(2018, 6, 20, 13, 30), content: 'dinar' },
        { date: new Date(2018, 6, 20, 20, 30), content: 'sopar' },
      ];

      return {
        mealsOfTheDay: mealsOfTheDay.map(m => ({
          start: m.date,
          title: m.content,
        })),
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
  };
</script>

<style>
  @import '../node_modules/fullcalendar/dist/fullcalendar.css';
  @import 'https://bootswatch.com/4/cerulean/bootstrap.min.css'; /* https://fullcalendar.io/releases/fullcalendar/3.9.0/demos/themes.html */
</style>

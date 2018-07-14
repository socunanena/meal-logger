<template>
  <div>
    <form v-on:submit.prevent="addMeal()">
      <input title="Date" v-model="date" />
      <input title="Content" v-model="content" />
      <button type="submit" title="go!" />
    </form>
  </div>
</template>

<script>
  export default {
    name: 'Calendar',
    data: () => ({
      date: null,
      content: null,
      meals: [],
    }),
    computed: {},
    methods: {
      addMeal() {
        this.meals.push({
          timestamp: new Date(this.date),
          content: this.content,
        });
      },
    },
  };
</script>

<style scoped>
</style>

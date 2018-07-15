<template>
  <div>
    <form v-on:submit.prevent="$emit('add-meal', { date, content })">
      <input title="Date" v-model="date" />
      <input title="Content" v-model="content" />
      <button type="submit" title="go!" />
    </form>
  </div>
</template>

<script>
  export default {
    name: 'MealInput',
    data: () => ({
      date: undefined,
      content: undefined,
    }),
  };
</script>

<style scoped>
</style>

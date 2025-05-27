<template>
  <button type="button" class="btn btn-primary">Primary</button>
  <h1> {{  title }}</h1>
  <ListMemes />
</template>

<script>


import ListMemes from './components/ListMemes.vue';

export default {
  name: "App",
  components: {
    ListMemes,
  },
};
</script>

<style></style>

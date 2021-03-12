<template>
  <div id="app">
    <DebitCard/>
  </div>
</template>

<script>
import DebitCard from "./components/DebitCard.vue";

export default {
  name: "App",
  components: {
    DebitCard,
  },
  methods: {},
};
</script>

<style>
#app {
  font: arial;
}
</style>

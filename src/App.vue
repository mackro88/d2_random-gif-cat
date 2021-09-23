<template>
  <div>
    <RandomGifCat />
  </div>
</template>

<script>
import RandomGifCat from "./components/RandomGifCat.vue";

export default {
  name: "App",
  components: {
    RandomGifCat,
  },
};
</script>

<style lang="scss">
body{
  margin: 0;
  background: lightblue;

}
</style>

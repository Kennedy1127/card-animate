<template>
  <CardCarousel />
  <!-- <CardCarousel2 /> -->
</template>

<script>
import CardCarousel from "./components/CardCarousel.vue";
import CardCarousel2 from "./components/CardCarousel2.vue";

export default {
  name: "App",
  components: {
    CardCarousel,
    CardCarousel2,
  },
};
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>

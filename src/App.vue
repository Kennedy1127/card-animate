<template>
  <CardCarousel />
</template>

<script>
import CardCarousel from "./components/CardCarousel.vue";

export default {
  name: "App",
  components: {
    CardCarousel,
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

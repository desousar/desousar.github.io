<template>
  <div id="home" class="section">
    <Hero />
  </div>
</template>

<script>
import Hero from './../components/Hero.vue';

export default {
  name: 'Home',
  components: {
    Hero
  }
};
</script>

<style scoped>
.section {
  background-color: #63bce5;
}
</style>

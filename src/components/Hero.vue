<template>
  <div
    class="hero"
    ref="target"
    :style="{
      transform: cardTransform,
      transition: 'transform 0.25s ease-out'
    }"
  >
    <h1>Hi I'm</h1>
    <h2 class="name">
      <div>Benoît&nbsp;</div>
      <div>DE SOUSA</div>
    </h2>
    <div @click="scrollToAboutMe" class="job">
      <h3>Web Developer</h3>
    </div>
  </div>
</template>

<script>
import { useMouseInElement } from '@vueuse/core';
import { ref, computed, onMounted } from 'vue';
import EventBus from './../event-bus';

export default {
  name: 'Hero',
  setup() {
    onMounted(() => {
      EventBus.on('menuIsOpened', isOpen => {
        menuIsOpen.value = isOpen;
      });
    });

    let menuIsOpen = ref(false);

    const target = ref(null);
    const { elementX, elementY, isOutside, elementHeight, elementWidth } =
      useMouseInElement(target);

    const cardTransform = computed(() => {
      if (menuIsOpen.value) {
        return '';
      }

      const MAX_ROTATION = 25;

      const rX = (
        MAX_ROTATION / 2 -
        (elementY.value / elementHeight.value) * MAX_ROTATION
      ).toFixed(2); // handles x-axis

      const rY = (
        MAX_ROTATION / 2 -
        (elementX.value / elementWidth.value) * MAX_ROTATION
      ).toFixed(2); // handles y-axis

      return isOutside.value
        ? ''
        : `perspective(${elementWidth.value}px) rotateX(${rX}deg) rotateY(${rY}deg)`;
    });

    function scrollToAboutMe() {
      document.getElementById('aboutMe').scrollIntoView({ behavior: 'smooth' });
    }

    return {
      target,
      cardTransform,
      scrollToAboutMe
    };
  }
};
</script>

<style scoped>
.hero {
  justify-content: center;
  width: 80%;
  padding: 16px;
  box-shadow: 10px 5px 5px #34495e;
}
h1 {
  margin: 0;
  font-size: 40px;
}
h2.name {
  margin: 0;
  font-size: 65px;
  display: flex;
  flex-wrap: wrap;
}
.job {
  cursor: pointer;
  margin: 1.4em auto 0 auto;
  padding: 1em;
  width: 75%;
  justify-content: center;
  color: #1c1c1c;
  transition: all 0.3s ease-in-out;
  z-index: 2;
  border-radius: 50px;
}
.job:hover {
  background-color: #3498db;
}
h3 {
  text-align: center;
  margin: 0;
  font-size: 30px;
}
</style>

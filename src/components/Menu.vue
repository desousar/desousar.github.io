<template>
  <svg
    version="1.1"
    id="Layer_1"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    x="0px"
    y="0px"
    viewBox="0 0 24 24"
    xml:space="preserve"
    class="menu"
    @click="openSlideMenu()"
  >
    <path d="M3,18h18v-2H3V18z M3,13h18v-2H3V13z M3,6v2h18V6H3z"></path>
  </svg>
  <transition name="slide">
    <div class="sidenav" v-show="showSlideMenu">
      <a @click="closeSlideMenu()" class="closebtn">&times;<i></i></a>
      <a href="#home"><b>Me</b></a>
      <a href="#aboutMe"><b>About Me</b></a>
      <a href="#"><b>My Work</b></a>
    </div>
  </transition>
  <transition name="blur">
    <div
      @click="showSlideMenu = false"
      class="blur-div"
      v-show="showSlideMenu"
    ></div>
  </transition>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const showSlideMenu = ref(false);
    function openSlideMenu() {
      showSlideMenu.value = true;
    }
    function closeSlideMenu() {
      showSlideMenu.value = false;
    }

    return {
      showSlideMenu,
      openSlideMenu,
      closeSlideMenu
    };
  }
};
</script>

<style scoped>
.sidenav {
  height: 100vh;
  width: 40%;
  position: fixed;
  z-index: 10;
  top: 0;
  right: 0;
  background-color: #150737;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.sidenav a {
  padding: 12px;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}

.sidenav a:hover {
  color: #f1f1f1;
}

.sidenav .closebtn {
  cursor: pointer;
  font-size: 40px;
  color: white;
  display: flex;
  flex-direction: row-reverse;
  width: 80%;
  height: 12vh;
  align-items: center;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease-out;
}
.slide-enter-from,
.slide-leave-to {
  transform: translateX(80vw);
}

.blur-div {
  backdrop-filter: blur(3px);
  z-index: 5;
  position: fixed;
  width: 100%;
  left: 0;
  top: 0;
  height: 100vh;
}
.blur-enter-active,
.blur-active,
.blur-leave-active {
  transition: all 0.3s ease;
}
.blur-enter-from,
.blur-leave-to {
  opacity: 0;
}
</style>

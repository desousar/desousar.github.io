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
    v-on:click="openSlideMenu()"
  >
    <path
      d="M3,18h18v-2H3V18z M3,13h18v-2H3V13z M3,6v2h18V6H3z"
      class="st2"
    ></path>
  </svg>
  <transition name="slide">
    <div id="slide-menu" v-show="showSlideMenu">
      <div id="mySidenav" class="sidenav">
        <a @click="closeSlideMenu()" class="closebtn">&times;<i></i></a>
        <a href="#"><b>About Me</b></a>
        <a href="#"><b>Work</b></a>
        <a href="#"><b>Find Me</b></a>
      </div>
    </div>
  </transition>
  <transition name="blur">
    <div
      @click="showSlideMenu = false"
      class="blur-div"
      v-if="showSlideMenu"
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

.slide-leave-active {
  transition: all 0.5s ease;
}
.slide-leave-to {
  opacity: 0;
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
.blur-enter-active {
  animation: b-slide 0.5s;
}
@keyframes b-slide {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.blur-leave-active {
  transition: all 1s ease;
}
.blur-leave-to {
  opacity: 0;
}
</style>

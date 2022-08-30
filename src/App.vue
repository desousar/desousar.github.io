<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <div class="logo" @click="scrollToTop">bds</div>
  <Menu />
  <Home />
  <about-me />
</template>

<script>
import Menu from './components/Menu.vue';
import Home from './section/Home.vue';
import AboutMe from './section/AboutMe.vue';

export default {
  name: 'App',
  components: {
    Menu,
    Home,
    AboutMe
  },
  setup() {
    function scrollToTop() {
      document.getElementById('app').scrollIntoView({ behavior: 'smooth' });
    }
    return {
      scrollToTop
    };
  }
};
</script>

<style>
body {
  overflow-x: hidden;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.logo {
  top: 0;
  left: 0;
}
.menu {
  right: 0;
  width: 30px;
  z-index: 10;
}
.logo,
.menu {
  z-index: 1;
  margin: 2em;
  cursor: pointer;
  position: fixed;
}
.section {
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

@media screen and (max-width: 700px) {
  h2.name {
    font-size: 55px !important;
    display: inline !important;
  }

  .sidenav {
    width: 50% !important;
  }

  .job {
    width: max-content !important;
  }
}
</style>

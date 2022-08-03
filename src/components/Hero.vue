<template>
  <div class="hero">
    <h1>Hi I'm</h1>
    <h2 class="name">
      <div>Benoît&nbsp;</div>
      <div>DE SOUSA</div>
    </h2>
    <div class="job">
      <h3>Web Developer</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hero'
};
</script>

<style scoped>
.hero {
  justify-content: center;
  width: 80%;
}
h1 {
  margin: 0;
  font-size: 40px;
}
h2.name {
  margin: 0;
  font-size: 65px;
  display: flex;
}
.job {
  cursor: pointer;
  margin: 1.4em auto 0 auto;
  padding: 1em;
  width: 75%;
  justify-content: center;
  background-color: #7ed5ea;
  color: #1c1c1c;
  transition: all 0.3s ease-in-out;
  z-index: 2;
  border-radius: 50px;
}
.job:hover {
  background-color: #3778c2;
}
h3 {
  text-align: center;
  margin: 0;
  font-size: 30px;
}
</style>

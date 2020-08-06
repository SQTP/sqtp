<template>
  <div class="building">
    <div id="app">
      <router-view />

    </div>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
  .building {
    justify-content: center;
    align-items: center;
    background-image: url('assets/login-background.jpg');
    background-size: 100% 100%;
    height: 100%;
    background-size: cover;
  }
</style>


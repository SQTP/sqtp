<template>
  <div id="app">
    <router-view/>
    <div style="margin:0 auto;" class="grey--text">Presented by 李智,刘泽铖,徐正浩,李蕴祺,陶嘉辰,俞晓锋,于嘉伟,宋逸群,李俊松</div>
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
}
  .building {
    justify-content: center;
    align-items: center;
    background-image: url('../static/bg.jpg');
    background-size: 100% 100%;
    height: 100%;
    background-size: cover;
  }
</style>


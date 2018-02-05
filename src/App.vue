<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!--<hello></hello>-->
    <!--<el-button type="success">成功按钮</el-button>-->
    <router-view/>
  </div>
</template>

<script>import Hello from './components/Hello.vue'

export default {
  name: 'App',
  components: {
    Hello
  }
}
</script>

<style>
  @import "./assets/css/public.css";
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>

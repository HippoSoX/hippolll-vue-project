<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1>计算器</h1>
    <Calculator/>
    <GetResponse/>
  </div>
</template>

<script>
import Calculator from './components/Calculator'
import GetResponse from './components/GetResponse'

export default {
  name: 'App',
  components: {
    Calculator,
    GetResponse
  }
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
</style>

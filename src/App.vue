<template>
<div id="App">
  <h1>Vue Calculator</h1>
  <Calculator />
</div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    Calculator
  }
}
</script>

<style>
#app {
  font-family: 'Oswald', sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 20px;
}
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  background-color: #42b983;
}
h1 {
  background-color: #42b983;
  margin-bottom: 10px;
}
</style>

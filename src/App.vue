<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Calculator msg="Calculated Calculator"/>
      <CalcScreen></CalcScreen>
  </div>
</template>

<script defer>
import Calculator from './components/Calculator.vue'
import CalcScreen from './components/CalcScreen.vue'

export default {
  name: 'app',
  components: {
    Calculator,
    CalcScreen
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
  position: relative;
}

</style>

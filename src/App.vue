<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Formulario msg="Bienvenido al mejor generador de gif de gatitos de la historia!"/>
  </div>
</template>

<script>
import Formulario from './components/Formulario.vue'

export default {
  name: 'App',
  components: {
    Formulario
  }
}
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

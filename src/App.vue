<template>
  <img alt="Vue logo" src="./assets/logo.png">
    <h1>Would you rather?</h1>

    <h2>Please make your choice!</h2>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'WouldYouRather',
  components: {
    WouldYouRather
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

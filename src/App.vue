<template>
  <Countdown />
</template>

<script>
import Countdown from './components/Countdown.vue';

export default {
  name: 'App',
  components: {Countdown}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 100px;
}
</style>

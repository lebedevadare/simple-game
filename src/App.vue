<template>
  <div id="app">
    <GameBody />
  </div>
</template>

<script>
import GameBody from './components/GameBody.vue'

export default {
  name: 'App',
  components: {
    GameBody
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

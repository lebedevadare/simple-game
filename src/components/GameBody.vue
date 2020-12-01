<template>
  <div class = "wrapper">
    <h1>Simon Says</h1>
    <div class = "game-board">
      <div class = "simon">
        <ul>
          <li class = "tile red" data-tile = "1"></li>
          <li class = "tile blue" data-tile = "2"></li>
          <li class = "tile yellow" data-tile = "3"></li>
          <li class = "tile green" data-tile = "4"></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GameBody',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang = "scss">
</style>

<template>
  <div class = "container">
   <game-tiles></game-tiles>
    <game-options></game-options>
  </div>
</template>

<script>
import GameOptions from "@/components/GameOptions";
import GameTiles from "@/components/GameTiles";

export default {
  name: "GameBody",
  components: {
    GameOptions,
    GameTiles

  }
}
</script>

<style scoped lang="scss">
.container {
  width: 810px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
}
</style>
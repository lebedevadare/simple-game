<template>
  <div>

    <div class = "container">
      <tiles></tiles>
      <div class = "wrapper">
        <div class = "game-info">
          <h2 class = "game-info__heading">Раунд: <span>0</span></h2>
          <button class = "game-info__button">Start</button>
          <p data-action = "lose">Извени, ты проиграл после <span></span> раунда!</p>
        </div>

        <div class = "game-options">
          <h2 class = "game-options__header">Уровень:</h2>
          <input class = "game-options__input" type = "radio" name = "mode" value = "easily" checked>Легкий<br>
          <input class = "game-options__input" type = "radio" name = "mode" value = "middle">Средний<br>
          <input class = "game-options__input" type = "radio" name = "mode" value = "complicated">Сложный<br>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Tiles from "@/components/Tiles";

export default {
  name: "Game",
  components: {
    Tiles
  }
}
</script>

<style scoped lang = "scss">
.container {
  width: 810px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
}

.game-info {
  margin-top: 10px;
  margin-left: 30px;
}

.game-info__button {
  width: 5em;
  box-sizing: border-box;
  font-size: 1.4em;
  border-radius: 10px 10px 10px 10px;
  background: #6DABE8;
  border: none;
  padding: 0.3em 0.6em;

  &:hover {
    background: #78BCFF;
  }

}

.game-heading__info {
  font-size: 24px;
    margin: 0;
    margin-top: 30px;

}

.game-options {
  &__header {
    font-size: 28px;
  }

  &__input {
    margin-right: 10px;
  }

}
</style>

<template>
  <div>
    <div class = "game-info">
      <h2 class = "game-heading__info game-heading__info--indent">Раунд: <span>0</span></h2>
      <button class = "game-button__action">Start</button>
      <p data-action = "lose">Извени, ты проиграл после <span></span> раунда!</p>
    </div>

    <div class = "game-options">
      <h2 class="game-options__header">Уровень:</h2>
      <input type = "radio" name = "mode" value = "easily" checked>Легкий<br>
      <input type = "radio" name = "mode" value = "middle">Средний<br>
      <input type = "radio" name = "mode" value = "complicated">Сложный<br>
    </div>
  </div>
</template>

<script>
export default {
  name: "GameOptions"
}
</script>

<style scoped lang="scss">
.game-info {
  margin-top: 90px;
}

.game-button__action {
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
.game-heading__info{
  font-size: 24px;
  &--indent{
    margin: 0;
    margin-top: 30px;
  }
}

.game-options__header{
font-size: 28px;
}
.game-options input[type="radio"] {
  margin-right: 10px;
}
</style>

<template>
  <div>

      <div class = "game-body">
        <ul class = "game-list">
          <li class = "game-list__tile game-list__tile--red"></li>
          <li class = "game-list__tile game-list__tile--blue"></li>
          <li class = "game-list__tile game-list__tile--yellow"></li>
          <li class = "game-list__tile game-list__tile--green"></li>
        </ul>
      </div>
      <game-level></game-level>
    </div>
</template>

<script>


export default {
  name: 'GameTiles'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang = "scss">
ul {
  list-style: none;
}

ul, li {
  padding: 0;
  margin: 0;
}


.container {
  width: 810px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
}

.game-list {
  background: #fff;
  position: relative;
  float: left;
  margin-right: 3em;
  width: 302px;
  height: 295px;
  -webkit-border-radius: 150px 150px 150px 150px;
  border-radius: 150px 150px 150px 150px;
  -moz-box-shadow: 2px 1px 12px #aaa;
  -webkit-box-shadow: 2px 1px 12px #aaa;
  -o-box-shadow: 2px 1px 12px #aaa;
  box-shadow: 2px 1px 12px #aaa;

  &__tile {
    opacity: 0.6;
    -webkit-transition: opacity 250ms ease;
    -moz-transition: opacity 250ms ease;
    -ms-transition: opacity 250ms ease;
    -o-transition: opacity 250ms ease;
    transition: opacity 250ms ease;
  }

  &__tile--red, &__tile--blue, &__tile--yellow, &__tile--green {
    height: 290px;
    -webkit-border-radius: 150px 150px 150px 150px;
    border-radius: 150px 150px 150px 150px;
    position: absolute;
    text-indent: 10000px;
  }

  &__tile--red, &__tile--blue, &__tile--yellow, {
    &:hover {
      border: 2px solid black;
    }
  }

  &__tile--red {
    background: #FF5643;
    clip: rect(0px, 300px, 150px, 150px);
    width: 296px;
  }

  &__tile--blue {
    background: dodgerblue;
    clip: rect(0px, 150px, 150px, 0px);
    width: 300px;
  }

  &__tile--yellow {
    background: #FEEF33;
    clip: rect(150px, 150px, 300px, 0px);
    width: 300px;
  }

  &__tile--green {
    background: #BEDE15;
    clip: rect(150px, 300px, 300px, 150px);
    width: 296px;
  }
}


.game-list__tile.lit {
  opacity: 1;
}
</style>

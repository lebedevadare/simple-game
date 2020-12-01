<template>
  <div>

    <div class = "container">
      <tiles @click = "onClick" ref = "tiles"/>
      <div class = "wrapper">
        <div class = "game-info">
          <h2 class = "game-info__heading">Раунд: <span>{{ round }}</span></h2>
          <button class = "game-info__button" @click = "start()" :disabled = "status === 'animation'">Start</button>
          <p v-if = "status === 'lost'">Извини, ты проиграл после <b>{{ round }}</b> раунда!</p>
        </div>

        <div class = "game-options">
          <h2 class = "game-options__header">Уровень:</h2>
          <input v-model = "difficulty" class = "game-options__input" type = "radio" name = "mode" value = "easily"
                 checked>Легкий<br>
          <input v-model = "difficulty" class = "game-options__input" type = "radio" name = "mode" value = "middle">Средний<br>
          <input v-model = "difficulty" class = "game-options__input" type = "radio" name = "mode"
                 value = "complicated">Сложный<br>
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
  },
  data() {
    return {
      tiles: ['red', 'blue', 'green', 'yellow'],
      sequence: {
        game: [],
        round: []
      },
      round: 0,
      difficulty: 'easy',
      status: 'idle',
    }
  }, computed: {
    animationDelay() {
      if (this.difficulty === 'easy') {
        return 1500
      } else if (this.difficulty === 'medium') {
        return 1000
      } else {
        return 400
      }
    }
  },
  methods: {
    start() {
      this.status = 'idle';
      this.sequence = {
        game: [],
        round: []
      };
      this.round = 0;
      this.nextRound();
    },

    nextRound() {
      this.status = 'idle';
      this.sequence.game.push(this.randomTile())
      this.sequence.round = this.sequence.game.slice(0)
      this.round += 1;
      this.animate();
    },

    endGame() {
      this.status = 'lost';
    }, animate() {
      this.status = 'animation'
      this.sequence.game.forEach((tile, index) => {
        setTimeout(() => {
          this.$refs.tiles.lightUp(tile);
          if (index === this.sequence.game.length - 1) {
            this.status = 'play';
          }
        }, this.animationDelay * (index + 1))
      });
    },
    randomTile() {
      return this.tiles[Math.floor((Math.random() * this.tiles.length))];
    },
    onClick(tile) {
      if (this.status === 'play') {
        const correctTile = this.sequence.round.shift();
        if (correctTile === tile) {
          // Если все элементы были выбраны:
          if (this.sequence.round.length === 0) {
            this.nextRound();
          }
        } else {
          this.endGame();
        }
      }
    }
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

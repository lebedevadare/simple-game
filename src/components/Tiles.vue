<template>
  <div class = "tiles">
    <div v-for = "(value, tile) in tiles" @mousedown = "onMouseDown(tile)" @mouseout = "onMouseOut(tile)"
         @click = "onClick(tile)" :class = "tileClass(tile)" :key = "tile"></div>
  </div>
</template>


<script>


export default {
  data() {
    return {
      tiles: {
        red: {
          lighten: false,
        },
        blue: {
          lighten: false,
        },
        yellow: {
          lighten: false,
        },
        green: {
          lighten: false,
        },
      }
    }
  },
  methods: {
    tileClass(tile) {
      const classes = [
        'tiles__tile', `tiles__tile--${tile}`
      ];
      if (this.tiles[tile].lighten) {
        classes.push('tiles__tile--lighten')
      }
      return classes;
    },
    lightUp(tile) {
      this.playSound(tile);
      this.tiles[tile].lighten = true;
      setTimeout(() => {
        this.tiles[tile].lighten = false;
      }, 300)
    },
    playSound(tile) {
      const audio = new Audio(require(`../assets/audio/${tile}.mp3`));
      audio.play();
    },
    onClick(tile) {
      this.$emit('click', tile)
      this.playSound(tile);
      this.tiles[tile].lighten = false
    },
    onMouseDown(tile) {
      this.tiles[tile].lighten = true
    },
    onMouseOut(tile) {
      this.tiles[tile].lighten = false
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang = "scss">
.tiles {
	background: #fff;
	width: 302px;
	height: 295px;
	border-radius: 150px 150px 150px 150px;
	box-shadow: 2px 1px 12px #aaa;
	&__tile {
    cursor: pointer;
		opacity: 0.6;
		transition: opacity 250ms ease;
		&--lighten {
			opacity: 1;
		}
		&--red, &--blue, &--yellow, &--green {
			height: 290px;
			border-radius: 150px 150px 150px 150px;
			position: absolute;
			&:hover {
				border: 2px solid black
			}
		}
		&--red {
			background: #FF5643;
			clip: rect(0px, 300px, 150px, 150px);
			width: 296px;
		}

		&--blue {
			background: dodgerblue;
			clip: rect(0px, 150px, 150px, 0px);
			width: 300px;
		}

		&--yellow {
			background: #FEEF33;
			clip: rect(150px, 150px, 300px, 0px);
			width: 300px;
		}

		&--green {
			background: #BEDE15;
			clip: rect(150px,300px, 300px, 150px);
			width: 296px;
		}
	}
}
</style>

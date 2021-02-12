<template>
  <transition-group name="cell" tag="ul" class="puzzle__list">
    <li class="puzzle__list-item" v-for="(item, index) in items" :key="item">
      <PuzzleItem
        v-bind:item="item"
        :index="index"
        @click-item="go"
        :showNotice="showNotice"
        :lastClickedIndex="lastClickedIndex"
      />
    </li>
  </transition-group>
</template>

<script>
  export default {
    props: ['isNewGame'],

    data() {
      return {
        items: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 0],
        holeIndex: 15,
        move: {
          up: -4,
          right: 1,
          down: 4,
          left: -1,
        },
        showNotice: false,
        lastClickedIndex: null,
      }
    },

    watch: {
      isNewGame: function () {
        if (this.isNewGame) {
          this.items = this.shuffleArray(this.items).slice();
          // Если комбинация нерешаема, делаем её решаемой
          while (!this.isSolvable(this.items, this.holeIndex)) {
            this.swap(0, 1);
            // На случай, если индекс пустой клетки был 0 или 1
            this.serchHole(this.items);
          }
          this.$emit('started-game');
        }
      },
    },

    methods: {
      // Поиск индекса пустой клетки
      serchHole: function (arr) {
        this.holeIndex = arr.indexOf(0);
      },

      // Перемешивание массива
      shuffleArray: function (arr) {
        let j, temp;
        for (let i = arr.length - 1; i > 0; i--) {
          j = Math.floor(Math.random() * (i + 1));
          temp = arr[j];
          arr[j] = arr[i];
          arr[i] = temp;
        }
        this.serchHole(arr);

        return arr;
      },

      // Проверка на решаемость (см. Википедию)
      isSolvable: function (arr, holeIndex = this.serchHole(arr)) {
        const holeRow = Math.ceil((holeIndex + 1) / 4);
        let k = 0;

        arr.forEach((value, index) => {
          if (value !== 0) {
              for (let i = index + 1; i < arr.length; i++) {
                  if (arr[i] < value && arr[i] !== 0) {
                      k++;
                  }
              }
          }
        });

        return !((k + holeRow) % 2);
      },

      // Перемещение ячеек
      swap: function (i1, i2) {
        const temp = this.items[i1];
        this.$set(this.items, i1, this.items[i2]);
        this.$set(this.items, i2, temp);
      },

      // Проверка возможности перемещения
      isMoveAvailable: function (i) {
        switch (this.holeIndex - i) {
          case this.move.up:
            return this.move.up;
          case this.move.right:
            return this.move.right;
          case this.move.down:
            return this.move.down;
          case this.move.left:
            return this.move.left;
          default:
            return false;
        };
      },

      // Проверка на собранность
      isDone: function () {
        return !this.items.some(function(item, i) {
          return item > 0 && item-1 !== i;
        });
      },

      // Ход
      go: function (i) {
        if (this.isMoveAvailable(i)) {
          this.swap(i, this.holeIndex);
          this.holeIndex = i;
          this.$emit('make-move');
          if (this.isDone()) {
            this.$emit('win');
          }
        } else {
          this.lastClickedIndex = i;
          this.showNotice = true;
          setTimeout(() => { this.showNotice = false }, 500)
        }
      },
    },


  }
</script>

<style lang="scss" scoped>

  .puzzle__list {
    list-style-type: none;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(4, 1fr);
    gap: $puzzle-gap;
    padding: 1.5 * $puzzle-gap;
    background-color: $white-bg;
    border-radius: $border-radius;
    overflow: hidden;
  }

  .puzzle__list-item {
    position: relative;
    width: 100%;
    padding-bottom: 100%;
  }

  .cell-move {
    transition: transform .2s;
  }

  @include query($s) {
    .puzzle__list {
      gap: $puzzle-gap_sm;
      padding: 1.5 * $puzzle-gap_sm;
    }
  }

</style>

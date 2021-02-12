<template>
  <div class="container">
    <button
      :class="[
        'start-button',
        (isGameStarted & !isTimeOver & !isDone) ? '' : 'start-button_accented',
      ]"
      @click="startGame"
    >
      Новая игра
    </button>
    <Header>
      <template v-slot:steps>{{ steps }}</template>
      <template v-slot:time>{{ timeLeft }}</template>
    </Header>
    <div class="game-container">
      <Puzzle
        :isNewGame="isNewGame"
        @started-game="startedGame"
        @make-move="steps++"
        @win="handleWin"
      />
      <transition name="fade">
        <Notification
          v-show="!isGameStarted || isTimeOver || isDone"
          :isDone="isDone"
          :isTimeOver="isTimeOver"
          :isGameStarted="isGameStarted"
          :gameTime="gameTime"
        />
      </transition>
    </div>
  </div>
</template>

<script>
import Notification from './Notification.vue';
  export default {
  components: { Notification },
    data() {
      return {
        steps: 0,
        //  Для таймера
        currentTime: 0,
        maxTime: 900,
        counter: false,
        interval: null,
        // Для начала новой игры (trigger)
        isNewGame: false,
        // Для уведомлений
        isGameStarted: false,
        isDone: false,
        isTimeOver: false,
      }
    },

    computed: {
      timeLeft: function () {
        return this.formatTime(this.currentTime);
      },

      gameTime: function () {
        return this.formatTime(this.maxTime - this.currentTime);
      }
    },

    methods: {
      formatTime: function (time) {
        const sec = time % 60;
        const min = (time - sec) / 60;
        const checkFormat = (val) => val > 9 ? val : `0${val}`;
        return `${checkFormat(min)}:${checkFormat(sec)}`;
      },

      resetTimer: function () {
        clearInterval(this.interval);
        this.counter = false;
      },

      startTimer: function () {
        this.resetTimer();
        this.interval = setInterval(this.tick, 1000);
      },

      tick: function () {
        if (this.counter === false) {
          this.currentTime = this.maxTime;
          this.counter = true;
          this.isTimeOver = false;
        } else if (this.currentTime > 0) {
          this.currentTime --;
        } else {
          this.resetTimer();
          this.isTimeOver = true;
        }
      },

      startGame: function () {
        this.isNewGame = true;
        this.isGameStarted = true;
        this.startTimer();
        this.steps = 0;
        this.isDone = false;
      },

      startedGame: function () {
        this.isNewGame = false;
      },

      handleWin: function () {
        this.isGameStarted = false;
        this.isDone = true;
        this.resetTimer();
      }

    },
  }
</script>

<style lang="scss" scoped>

  .container {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 500px;
    min-height: 300px;
    padding: 20px;
    box-sizing: border-box;
    background-color: $white-bg;
    @include bg-blur;
    border: $white-border;
    border-radius: $border-radius;
    user-select: none;
  }

  .start-button {
    padding: 10px 15px;
    margin-left: auto;
    margin-right: 20px;
    background-color:  $white-bg-accent;
    border: $white-border;
    border-radius: $border-radius;
    color: $neutral-text;
    font-size: 20px;
    font-weight: 500;
    transition: $transition;
    cursor: pointer;
  }

  .start-button_accented {
    box-shadow: 0 0 10px $caution-tr;
  }

  .start-button:focus {
    outline: none;
  }

  .start-button:hover {
    box-shadow: 0 0 10px $dark-purple-tr;
  }

  .start-button:active {
    box-shadow: none;
  }

  .game-container {
    position: relative;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity 1s;
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

  @include query($s) {
    .container {
      padding: 10px;
    }

    .start-button {
      margin-right: 10px;
      font-size: 16px;
    }
  }

</style>

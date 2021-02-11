<template>
  <div class="container">
    <button class="start-button" @click="startGame">Новая игра</button>
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
// v-show="isGameStarted & !isTimeOver"
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
        // TODO -- поменять на false
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

      startTimer: function () {
        clearInterval(this.interval);
        this.counter = false;
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
          clearInterval(this.interval);
          this.counter = false;
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
      }

    },
  }
</script>

<style lang="scss" scoped>

  .container {
    display: flex;
    flex-direction: column;
    width: 100%;
    max-width: 550px;
    min-height: 300px;
    padding: 30px 20px 20px;
    box-sizing: border-box;
    background-color: $light-purple;
    box-shadow: 0 0 25px 15px $gray;
    border-radius: $border-radius;
  }

  .start-button {
    padding: 10px 15px;
    margin-left: auto;
    margin-right: 20px;
    background-color: $dark-purple;
    border: none;
    border-radius: $border-radius;
    color: $light-text;
    font-size: 20px;
    font-weight: 500;
    transition: $transition;
  }

  .start-button:focus {
    outline: none;
  }

  .start-button:hover {
    box-shadow: 0 0 5px #00000075;
    cursor: pointer;
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

</style>

<template>
  <div class="container">
    <button class="button" @click="startGame">Новая игра</button>
    <div class="header">
      <Logo />
      <div class="header__info">
        <p class="header__title">Ходов</p>
        <p class="header__text">0</p>
      </div>
      <div class="header__info">
        <p class="header__title">Время</p>
        <p class="header__text">{{ formatedTime }}</p>
      </div>
    </div>
    <Puzzle />
  </div>
</template>

<script>
  export default {
    data() {
      return {
        currentTime: 0,
        maxTime: 900,
        counter: false,
        interval: null,
      }
    },

    computed: {
      formatedTime: function () {
        const sec = this.currentTime % 60;
        const min = (this.currentTime - sec) / 60;
        const checkFormat = (val) => val > 9 ? val : `0${val}`;
        return `${checkFormat(min)}:${checkFormat(sec)}`;
      }
    },

    methods: {
      startGame: function () {
        clearInterval(this.interval);
        this.counter = false;
        this.interval = setInterval(this.tick, 1000);
      },

      tick: function () {
        if (this.counter === false) {
          this.currentTime = this.maxTime;
          this.counter = true;
        } else if (this.currentTime > 0) {
          this.currentTime --;
        } else {
          clearInterval(this.interval);
          this.counter = false;
        }
      }
    }
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

  .button {
    padding: 10px 15px;
    margin-left: auto;
    margin-right: 20px;
    background-color: $dark-purple;
    border: none;
    border-radius: $border-radius;
    color: $light-text;
    font-size: 20px;
    font-weight: 500;
    transition: .2s linear;
  }

  .button:focus {
    outline: none;
  }

  .button:hover {
    box-shadow: 0 0 5px #00000075;
  }

  .button:active {
    box-shadow: none;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
  }

  .header__info {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-width: 90px;
    min-height: 75px;
    padding: 10px 5px;
    margin-left: 10px;
    box-sizing: border-box;
    background-color: $dark-purple;
    border-radius: $border-radius;
    color: $light-text;
  }

  .header__title {
    font-size: 16px;
  }

  .header__text {
    font-size: 20px;
    font-weight: 500;
  }

  .header__info:first-of-type {
    margin-left: 0;
  }

</style>

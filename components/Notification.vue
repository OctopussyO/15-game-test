<template>
  <div class="notice">
    <!-- TODO -- Переделать -- не выдерживает переполнения контентом :(
      Хотя тут и не красиво будет растягивать контейнер -->
    <div class="notice__text-wrapper" v-if="!isGameStarted & !isDone">
      <p class="notice__text">Начните новую игру</p>
    </div>

    <div class="notice__text-wrapper" v-if="!isGameStarted & isDone">
      <p class="notice__text">Вы выиграли!</p>
      <p class="notice__text">Время: {{ gameTime }}</p>
    </div>

    <div class="notice__text-wrapper" v-if="isTimeOver">
      <p class="notice__text">Время вышло!</p>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['isGameStarted', 'isDone', 'isTimeOver', 'gameTime'],
  }
</script>

<style lang="scss" scoped>

  .notice {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 5px;
    background-color: #ffffff90;
    border-radius: $border-radius;
    overflow: hidden;
  }

  .notice__text-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    height: 100%;
  }

  .notice__text {
    color: $neutral-text;
    font-size: 36px;
    font-weight: 500;
  }

  @media screen and (max-width: 600px) {
    .notice__text {
      font-size: 24px;
    }
  }

</style>

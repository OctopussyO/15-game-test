<template>
  <div class="container">
    <div class="header">
      <p class="header__logo">15</p>
      <div class="header__info">
        <p class="header__title">Ходов</p>
        <p class="header__text">0</p>
      </div>
      <div class="header__info">
        <p class="header__title">Время</p>
        <p class="header__text">00:00</p>
      </div>
    </div>
    <ul class="puzzle">
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          1
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          2
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          3
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          1
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          2
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          3
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          1
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          2
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          3
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          1
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          2
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          3
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          1
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          2
        </p>
      </li>
      <li class="puzzle__item-wrapper">
        <p class="puzzle__item">
          3
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
  .container {
    width: 100%;
    max-width: 550px;
    min-height: 300px;
    padding: 30px 20px 20px;
    box-sizing: border-box;
    background-color: $light-purple;
    box-shadow: 0 0 25px 15px $gray;
    border-radius: $border-radius;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 20px;
    padding-right: 20px;
    padding-bottom: 20px;
  }

  .header__logo {
    margin-right: auto;
    color: $dark-text;
    font-size: 64px;
    line-height: 1;
    font-weight: 700;
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

  .puzzle {
    list-style-type: none;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(4, 1fr);
    gap: $puzzle-gap;
    padding: 15px;
    background-color: $dark-purple;
    border-radius: $border-radius;
    overflow: hidden;
  }

  .puzzle__item-wrapper {
    position: relative;
    width: 100%;
    padding-bottom: 100%;
    background-color: $light-purple;
    border-radius: $border-radius;
    transition: box-shadow .2s linear;
    cursor: pointer;
  }

  .puzzle__item {
    position: absolute;
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    color: $dark-text;
    font-size: 32px;
    font-weight: 500;
    user-select: none;
  }

  .puzzle__item-wrapper:hover {
    box-shadow: 0 0 $puzzle-gap #00000075;
  }

</style>

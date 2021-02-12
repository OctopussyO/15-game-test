<template>
  <div class="header">
    <Logo />
    <div class="header__info">
      <p class="header__title">Ходов</p>
      <p class="header__text">
        <slot name="steps" />
      </p>
    </div>
    <div class="header__info">
      <p class="header__title">Время</p>
      <p class="header__text">
        <slot name="time" />
      </p>
    </div>
  </div>
</template>

<style lang="scss" scoped>

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
    background-color: $white-bg-accent;
    border-radius: $border-radius;
    color: $neutral-text;
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

  @media screen and (max-width: 600px) {
    .header {
      padding: 10px;
    }

    .header__info {
      min-width: 70px;
      min-height: 55px;
    }

    .header__title {
      font-size: 14px;
    }

    .header__text {
      font-size: 16px;
    }
  }

</style>

<template>
  <li class="puzzle__item-wrapper">
    <p class="puzzle__item">
      {{ item }}
    </p>
  </li>
</template>

<script>
  export default {
    props: ['item'],
  }
</script>

<style lang="scss" scoped>
  .puzzle__item-wrapper {
    position: relative;
    width: 100%;
    padding-bottom: 100%;
    background-color: $light-purple;
    border-radius: $border-radius;
    transition: box-shadow .2s linear;
    cursor: pointer;
  }

  .puzzle__item-wrapper:hover {
    box-shadow: 0 0 $puzzle-gap #00000075;
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

</style>

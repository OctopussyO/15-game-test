<template>
  <h1 class="logo">
    15
  </h1>
</template>

<style lang="scss" scoped>

  .logo {
    margin-right: auto;
    color: $dark-text;
    font-size: 64px;
    line-height: 1;
    font-weight: 700;
    letter-spacing: -5px;
  }

  @include query($s) {
    .logo {
      font-size: 56px;
    }
  }

</style>

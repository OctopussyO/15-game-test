<template>
  <ul class="puzzle">
    <PuzzleItem v-for="item in items" :key="item" v-bind:item="item" />
  </ul>
</template>

<script>
  export default {
    data() {
      return {
        items: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15],
      }
    },

  }
</script>

<style lang="scss" scoped>

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

</style>

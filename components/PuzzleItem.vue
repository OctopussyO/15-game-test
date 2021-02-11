<template>
  <button
    :class="['puzzle__item', this.item === '' ? 'puzzle__item_hidden' : '']"
    @click="$emit('click-item', index)"
  >
    {{ item }}
    <transition name="fade">
      <span v-if="showNotice & lastClickedIndex === index" class="puzzle__notice">
        &#10006;
      </span>
    </transition>
  </button>
</template>

<script>
  export default {
    props: ['item', 'index', 'showNotice', 'lastClickedIndex'],
  }
</script>

<style lang="scss" scoped>
  .puzzle__item {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: $light-purple;
    border-radius: $border-radius;
    border: none;
    color: $dark-text;
    font-size: 32px;
    font-weight: 500;
    transition: box-shadow $transition;
    cursor: pointer;
  }

  .puzzle__item_hidden {
    visibility: hidden;
  }

  .puzzle__item:hover {
    box-shadow: 0 0 $puzzle-gap #00000075;
  }

  .puzzle__item:focus {
    outline: none;
  }

  .puzzle__item:hover:active {
    box-shadow: none;
  }

  .puzzle__notice {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: $caution-text;
    font-size: 2em;
    line-height: 1;
    font-weight: 500;
    opacity: .8;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity $transition;
  }

  .fade-enter, .fade-leave-to {
    opacity: 0;
  }

  @media screen and (max-width: 600px) {
    .puzzle__item {
      font-size: 24px;
    }
    
    .puzzle__notice {
      font-size: 1.5em;
    }
  }


</style>

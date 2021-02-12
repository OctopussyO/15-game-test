<template>
  <div class="page__container">
    <Widget />
  </div>
</template>

<script>
import Widget from '~/components/Widget.vue';
export default {
  components: { Widget },
};
</script>

<style lang="scss">

  .page__container {
    padding: 16px;
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    background-image: linear-gradient(to top, #3b41c5 0%, #a981bb 49%, #ffc8a9 100%);
  }

</style>

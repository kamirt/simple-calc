<template lang="html">
  <div class="plus">
    <div class="plus__row">
      <div></div>
      <div></div>
    </div>
    <div class="plus__row">
      <div></div>
      <div></div>
    </div>
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
  .plus {
    width: 60px;
    &__row {
      display: flex;
    }
    &__row div{
      height: 30px;
      flex: 1 1 auto;
    }
    &__row div:last-child {
      border-left: 1px solid grey;
    }
    &__row:last-child {
      border-top: 1px solid grey;
    }
  }
</style>

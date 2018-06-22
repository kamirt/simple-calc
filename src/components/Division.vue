<template lang="html">
  <div class="division">
    <InputDiv
      div-type="numerator"
      ref="numerator"
      v-model="division.numerator"
      @input="change" />
    <InputDiv
      div-type="denominator"
      ref="denominator"
      v-model="division.denominator"
      @input="change" />
  </div>
</template>

<script>
import InputDiv from "./InputDiv";

export default {
  props: ['division'],
  components: {
      InputDiv
  },
  methods: {
    change (val, itype) {
      const obj = {
        numerator: this.$refs.numerator.value,
        denominator: this.$refs.denominator.value
      };
      obj[itype] = val;
      this.$emit('input', obj)
    },
  }
}
</script>

<style lang="scss" scoped>
  .division {
    padding: 10px;
  }
</style>

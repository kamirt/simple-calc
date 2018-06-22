<template lang="html">
  <div class="div-input" :div-type="divType">
    <input @input="change" type="text" name="" :value="value">
  </div>
</template>

<script>
export default {
  props: ['divType', 'value'],
  data () {
    return {
      reg: /^\d{1,2}$/
    }
  },
  methods: {
    change (e) {
      const val = e.target.value;
      if ( this.reg.test(val) ) {
        this.$emit('input', e.target.value, this.$props.divType)
        return;
      }
      e.target.value = this.$props.value;
    }
  }
}
</script>

<style lang="scss">
  .div-input {
    padding: 20px;
    & input {
      height: 50px;
      width: 60px;
      background: #efefef;
      border: none;
      outline: none;
      font-size: 50px;
      text-align: center;
    }
  }
  .div-input[div-type="numerator"] {
    border-bottom: 1px solid grey;
  }
</style>

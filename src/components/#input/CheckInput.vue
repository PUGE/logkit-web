<template>
  <div class="check-input">
    <div class="text-bar">
      <span v-if="must" class="must">*</span>
      <span>{{label}}:</span>
    </div>
    <div class="right">
      <CheckBox class="check-box" :value="value" @input="updateValue" :size="11" />
      <span>{{text}}</span>
    </div>
  </div>
</template>

<script>
import CheckBox from 'check-puge'
export default {
  props: {
    value: null,
    must: {
      default: false,
      type: Boolean
    },
    text: String,
    label: {
      default: '',
      type: String
    }
  },
  components: {
    CheckBox
  },
  created () {
    if (this.value) this.$emit('input', this.value)
  },
  methods: {
    updateValue (event) {
      this.$emit('input', event)
    }
  }
}
</script>

<style scoped>
  .check-input {
    display: flex;
  }
  .text {
    color: #000;
  }
  .label {
    color: rgba(0, 0, 0, 0.43);
  }
  .right {
    line-height: 26px;
    display: flex;
    color: rgba(0,0,0,.65);
    font-size: 12px;
    margin: 0 10px;
  }
  .right span {
    line-height: 30px;
  }
  .check-box {
    margin: 7px;
  }
</style>
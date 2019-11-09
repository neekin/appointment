<template>
  <div class='input'>
    {{text}}:
    <input :value="value"
           @input="$emit('input', $event.target.value)"
           :type='type'>
  </div>
</template>

<script>
export default {
  props: ['text', 'type', 'value']
}
</script>

<style lang="scss" scoped>
.input {
  font-size: 34rpx;
  color: #9a9a9a;
  border-bottom: 1rpx solid #ccc;
  width: 80%;
  margin: 0 auto;
  display: flex;
  padding-bottom: 30rpx;
  margin-top: 20px;
  font-weight: 300;
  input {
    padding-left: 1em;
  }
}
</style>

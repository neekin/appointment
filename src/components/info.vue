<template>
  <div class='input'>
    <span>{{text}}</span>
    <span>{{value}}</span>
  </div>
</template>

<script>
export default {
  props: ['text', 'value']
}
</script>

<style lang="scss" scoped>
.input {
  font-size: 28rpx;
  // color: #9a9a9a;
  border-bottom: 1rpx solid #ccc;
  width: 80%;
  margin: 0 auto;
  display: flex;
  padding-bottom: 30rpx;
  margin-top: 20px;
  font-weight: 300;
  display: flex;
  justify-content: space-between;
  span:nth-of-type(2) {
    color: #9a9a9a;
    width: 40%;
  }
}
</style>

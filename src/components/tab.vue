<template>
  <div class='tab'>
    <ul>
      <li v-for='item in items'
          :key="item.id"
          :class='item.id==active?"active":""'
          @click='change(item.id)'>
        {{item.value}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['items', 'active'],
  methods: {
    change (id) {
      this.$emit('changeActive', id)
    }
  }

}
</script>

<style lang="scss" scoped>
.tab {
  ul {
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 80rpx;
    line-height: 80rpx;
    background-color: #0094ff;
    li {
      padding: 0 8rpx;
      color: #fff;
      position: relative;
      font-size: 14px;
    }
    li.active {
      &::after {
        position: absolute;
        content: "";
        width: 100%;
        height: 4rpx;
        background-color: #fff;
        bottom: 0;
        left: 0;
      }
    }
  }
}
</style>

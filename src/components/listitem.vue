<template>
  <div class='listitem'
       @click="$emit('childClick',targetText.region_id)">
    <ul>
      <li>{{targetText.name}}</li>
      <li>活动完成率：{{targetText.activity_rate}}</li>
      <li>代表人数：{{targetText.rep_num}}</li>
      <li>锁定场次： {{targetText.lock_session}}</li>
      <li>执行次数：{{targetText.execution_session}}</li>
      <li>差异场次：{{targetText.difference_session}} </li>
      <li>活动目标：{{targetText.activity_target}}</li>
      <li>活动销量：{{targetText.activity_volume}}</li>
      <li>卡萨帝目标：{{targetText.casadi_target}}</li>
      <li>卡萨帝实际：{{targetText.casadi_actual}}</li>
      <li>完成率：{{targetText.casadi_rate}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  props: {
    target: {
      type: Object
    }
  },
  computed: {
    targetText () {
      const defaultText = {
        region_id: 0,
        name: '名称',
        activity_rate: 0, // 活动完成率
        rep_num: 0, // 代表人数
        lock_session: 0, // 锁定场次
        execution_session: 0, // 执行次数
        difference_session: 0, // 差异场次
        activity_target: 0, // 活动目标
        activity_volume: 0, // 活动销量
        casadi_target: 0, // 卡萨帝目标
        casadi_actual: 0, // 卡萨帝实际
        casadi_rate: 0 // 完成率
      }
      return Object.assign(defaultText, this.target || {})
    }
  }
}
</script>

<style lang="scss" scoped>
.listitem {
  ul {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    flex-wrap: wrap;
    padding-left: 0;
    li:nth-of-type(1) {
      font-weight: 900;
      color: #000;
    }
    li {
      height: 54rpx;
      line-height: 54rpx;
      text-align: center;
      list-style: none;
      flex: 0 0 33.3333%;
      font-size: 14px;
      box-sizing: border-box;
      color: #6c6c6c;
      // font-size: 10px;
    }
    li:nth-of-type(2) {
      flex: 0 0 66.6666%;
    }
    li:nth-of-type(3),
    li:nth-of-type(4),
    li:nth-of-type(5),
    li:nth-of-type(6),
    li:nth-of-type(7),
    li:nth-of-type(8),
    li:nth-of-type(9),
    li:nth-of-type(10),
    li:nth-of-type(11) {
      border-bottom: 1px solid #ccc;
    }
  }
}
</style>

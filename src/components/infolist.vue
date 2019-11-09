<template>
  <div class='listitem'>
    <ul>
      <li @click="$emit('childClick', serlist )">{{  targetText.serName|| targetText.repName|| targetText.name}}</li>
      <li></li>
      <li @click='goserinfo(targetText.serID || targetText.repID)'>查看详情</li>
      <li>代表人数：{{targetText.rep_number}}</li>
      <li>网络专员人数： {{targetText.network_number}}</li>
      <li>人均场次： {{ targetText.people_session}}</li>
      <li>锁定场次： {{targetText.lock_session}}</li>
      <li>执行次数：{{targetText.execution_session}}</li>
      <li>差异场次：{{targetText.difference_session}} </li>
      <li>活动目标：{{targetText.activity_target}}</li>
      <li>活动销量：{{targetText.activity_volume}}</li>
      <li>完成率：{{targetText.activity_rate}}</li>

      <li>卡萨帝目标：{{targetText.casartetarget}}</li>
      <li>卡萨帝实际：{{targetText.casarteActual}}</li>
      <li>完成率：{{targetText.casadi_rate}}</li>

      <li>场均目标：{{targetText.avg_target}}</li>
      <li>场均实际：{{targetText.avg_actual}}</li>
      <li>场均卡萨帝：{{targetText.avg_casadi}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // serlist: null
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
        id: 0,
        name: '名称',
        activity_rate: 0, // 活动完成率
        rep_number: 0, // 代表人数
        network_number: 0, // 网络代表人数
        people_session: 0, // 人均场次
        lock_session: 0, // 锁定场次
        execution_session: 0, // 执行次数
        difference_session: 0, // 差异场次
        activity_target: 0, // 活动目标
        activity_volume: 0, // 活动销量
        casadi_target: 0, // 卡萨帝目标
        casadi_actual: 0, // 卡萨帝实际
        casadi_rate: 0, // 完成率
        avg_target: 0, // 场均目标
        avg_actual: 0, // 场均实际
        avg_casadi: 0 // 场均卡萨帝
      }

      return Object.assign(defaultText, this.target || {})
    },
    serlist () {
      // console.log(this.targetText.serID)
      if (this.targetText.repID) {
        console.log(this.targetText)
        return { 'repID': this.targetText.repID, 'region_id': this.targetText.region_id }
      } else {
        return { 'serID': this.targetText.serID, 'region_id': this.targetText.region_id }
      }
    }
  },
  methods: {
    goserinfo (id) {
      let url = '/pages/serinfo/main'
      if (this.targetText.repID) {
        url = url + '?repID=' + id
      } else {
        url = url + '?serID=' + id
      }
      wx.navigateTo({ url: url })
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
    li:nth-of-type(3) {
      color: #ff0000;
    }
    li:nth-of-type(1),
    li:nth-of-type(2),
    li:nth-of-type(3) {
      border: none;
    }
    li {
      width: 33.333333%;
      height: 54rpx;
      line-height: 54rpx;
      text-align: left;
      list-style: none;
      flex: 0 0 33.3333%;
      font-size: 12px;
      box-sizing: border-box;
      color: #6c6c6c;
      border-bottom: 1px solid #ececec;
    }
  }
}
</style>

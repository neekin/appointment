<template>
  <div>
    <div class="title">服务商详情</div>
    <ul>
      <li>{{result.SERVICE_PROVIDER_NAME || result.REPRESENTATIVE_NAME}}</li>
      <li>
        <span>活动主题</span><span>{{result.ACTIVITY_NAME}}</span>
      </li>
      <li>
        <span>签约产业</span><span>
          {{ result.CONTRACTED_INDUSTRY}}</span>
      </li>

      <li>
        <span>整体活动目标</span><span>{{result.ACTIVITY_OVERALL_TARGET}}</span>
      </li>
      <li>
        <span>整体活动销量</span><span>{{result.ACTIVITY_OVERALL_SALES_VOLUME}}</span>
      </li>
      <li>
        <span>整体完成率</span><span>{{result.ACTIVITY_OVERALL_COMPLETION_RATE}}</span>
      </li>
      <li>

        <span>冰箱目标</span><span>{{result.REFRIGERATOR_TARGET}}</span>
      </li>
      <li>
        <span>冰箱实际</span><span>{{result.REFRIGERATOR_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.REFRIGERATOR_COMPLETION_RATE}}</span>
      </li>
      <li>

        <span>冷柜目标</span><span>{{result.FREEZER_TARGET}}</span>
      </li>
      <li>
        <span>冷柜实际</span><span>{{result.FREEZER_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.FREEZER_COMPLETION_RATE}}</span>
      </li>

      <li>
        <span>洗衣机目标</span><span>{{result.WASHING_MACHINE_TARGET}}</span>
      </li>
      <li>
        <span>洗衣机实际</span><span>{{result.WASHING_MACHINE_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.WASHING_MACHINE_COMPLETION_RATE}}</span>
      </li>
      <li>
        <span>空调目标</span><span>{{result.AIR_CONDITIONING_TARGET}}</span>
      </li>
      <li>
        <span>空调实际</span><span>{{result.AIR_CONDITIONING_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.AIR_CONDITIONING_COMPLETION_RATE}}</span>
      </li>
      <li>

        <span>热水器目标</span><span>{{result.WATER_HEATER_TARGET}}</span>
      </li>
      <li>
        <span>热水器实际</span><span>{{result.WATER_HEATER_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.WATER_HEATER_COMPLETION_RATE}}</span>
      </li>
      <li>

        <span>彩电目标</span><span>{{result.COLOR_TV_TARGET}}</span>
      </li>
      <li>
        <span>彩电实际</span><span>{{result.COLOR_TV_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.COLOR_TV_COMPLETION_RATE}}</span>
      </li>
      <li>
        <span>厨电目标</span><span>{{result.KITCHEN_APPLIANCE_TARGET}}</span>
      </li>
      <li>

        <span>厨电实际</span><span>{{result.KITCHEN_APPLIANCE_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.KITCHEN_APPLIANCE_COMPLETION_RATE}}</span>
      </li>
      <li>
        <span>卡萨帝目标</span><span>{{result.CASADI_TARGET}}</span>
      </li>
      <li>
        <span>卡萨帝实际</span><span>{{result.CASADI_ACTUAL}}</span>
      </li>
      <li>
        <span>完成率</span><span>{{result.CASADI_COMPLETION_RATE}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import request from '../../utils/request'
export default {
  data () {
    return {
      result: {}
    }
  },
  onLoad (options) {
    let url = '/atvtport/serviceproviderinfo/'
    if (options.serID) {
      url = url + 'findBySerId.do'
    } else {
      url = url + 'findByRepId.do'
    }
    request.request(url, 'POST', options).then(res => {
      this.result = res.data.data
      console.log(this.result)
    })
  }
}
</script>

<style lang="scss" scoped>
ul > li {
  width: 98%;
  margin: 0 auto;
  font-size: 14px;
  line-height: 60rpx;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  border-bottom: 1px solid #ccc;
  span {
    padding: 0 10rpx;
  }
  &:nth-of-type(1) {
    font-weight: 900;
  }
}
</style>

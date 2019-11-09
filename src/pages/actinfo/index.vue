<template>
  <div>
    <div class="title">
      区域服务商活动详情
    </div>
    <div class="info">
      <span>区域</span>
      <span>{{targetText.REGION}}</span>
    </div>
    <div class="info">
      <span>活动门店类型</span>
      <span>{{targetText.STORE_TYPE}}</span>
    </div>
    <div class="info">
      <span>活动门店名称</span>
      <span>{{targetText.STORE_NAME}} </span>
    </div>
    <div class="info">
      <span>活动门店8码</span>
      <span>{{targetText.STORE_CODE}}</span>
    </div>
    <div class="info">
      <span>老板姓名</span>
      <span>{{targetText.STORE_OWNER_NAME}} </span>
    </div>
    <div class="info">
      <span>老板电话</span>
      <span>{{ targetText.STORE_OWNER_TELEPHONE }} </span>
    </div>
    <div class="info">
      <span>上级理货商名称</span>
      <span>{{targetText.TALLY_NAME}}</span>
    </div>
    <div class="info">
      <span>上级理货商8码</span>
      <span>{{targetText.TALLY_CODE}}</span>
    </div>
    <div class="info">
      <span>理货商渠道</span>
      <span>{{targetText.TALLY_CHANNEL}}</span>
    </div>
    <div class="info">
      <span>活动主题</span>
      <span>{{targetText.ACTIVITY_THEME}}</span>
    </div>
    <div class="info">
      <span>活动类型</span>
      <span>{{targetText.ACTIVITY_TYPE}} </span>
    </div>
    <div class="info">
      <span>活动爆破开始时间</span>
      <span>{{targetText.BLASTING_START_TIME}}</span>
    </div>
    <div class="info">
      <span>活动爆破结束时间</span>
      <span>{{targetText.BLASTING_END_TIME}}</span>
    </div>
    <div class="info">
      <span>活动挂靠人姓名</span>
      <span>{{  targetText.EVENT_HOLDER_NAME}}</span>
    </div>
    <div class="info">
      <span>活动挂靠人电话</span>
      <span>{{targetText.EVENT_HOLDER_TELEPHONE}}</span>
    </div>
    <div class="info">
      <span>活动挂靠人产业</span>
      <span>{{targetText.EVENT_HOLDER_INDUSTRY}}</span>
    </div>
    <div class="info">
      <span>活动挂靠人工号</span>
      <span>{{targetText.EVENT_HOLDER_NUMBER}}</span>
    </div>
    <div class="info">
      <span>活动整体目标</span>
      <span>{{targetText.ACTIVITY_OVERALL_TARGET}}</span>
    </div>
    <div class="info">
      <span>卡萨帝整体目标</span>
      <span>{{targetText.CASADI_OVERALL_TARGET}}</span>
    </div>
    <div class="info">
      <span>冰箱目标</span>
      <span>{{targetText.REFRIGERATOR_TARGET}}</span>
    </div>
    <div class="info">
      <span>冷柜目标</span>
      <span>{{targetText.FREEZER_TARGET}}</span>
    </div>
    <div class="info">
      <span>洗衣机目标</span>
      <span>{{targetText.WASHING_MACHINE_TARGET}}</span>
    </div>
    <div class="info">
      <span>空调目标</span>
      <span>{{targetText.AIR_CONDITIONING_TARGET}}</span>
    </div>
    <div class="info">
      <span>热水器目标</span>
      <span>{{targetText.WATER_HEATER_TARGET}}</span>
    </div>
    <div class="info">
      <span>厨电目标</span>
      <span>{{targetText.KITCHEN_APPLIANCE_TARGET}}</span>
    </div>
    <div class="info">
      <span>彩电目标</span>
      <span>{{targetText.COLOR_TV_TARGET}}</span>
    </div>
    <div class="info">
      <span>净水目标</span>
      <span>{{targetText.CLEAN_WATER_TARGET}}</span>
    </div>
    <div class="info">
      <span>商空目标</span>
      <span>{{targetText.COMMERCIAL_SPACE_TARGET}}</span>
    </div>
    <div class="info">
      <span>启动会召开</span>

      <span>{{targetText.MEETING}}</span>
    </div>
    <div class="info">
      <span>战报输出</span>

      <span>{{targetText.BATTLE_OUTPUT}}</span>
    </div>
    <div class="info">
      <span>朋友圈转发</span>
      <span>{{targetText.FRIEND_SEND}}</span>
    </div>
    <div class="info">
      <span>累计数认筹实际</span>
      <span>{{targetText.CUMULATIVE_RECOGNITION_ACTUAL}}</span>
    </div>
    <div class="info">
      <span>累计数拆旧实际</span>
      <span>{{targetText.CUMULATIVE_DEMOLITION_ACTUAL}}</span>
    </div>
    <div class="info">
      <span>累计数进村数量</span>
      <span>{{targetText.CUMULATIVE_NUMBER_VILLAGES}}</span>
    </div>
    <div class="info">
      <span>认筹实际</span>
      {{targetText.RECRUIT_ACTUAL}}
    </div>
    <div class="info">
      <span>拆旧实际</span>
      {{targetText.DEMOLITION_ACTUAL}}
    </div>
    <div class="info">
      <span>进村数量</span>
      <span>{{targetText.NUMBER_VILLAGES}}</span>
    </div>
    <div class="info">
      <span>临促实到人数</span>
      <span>{{targetText.RECRUITMENT_NUMBER_ACTUAL}}</span>
    </div>
    <div class="info">
      <span>临促早会照片</span>
    </div>
    <div class="info">
      <img :src="url+targetText.PROMPT_MORNING_PICTURE"
           alt="">
    </div>
    <div class="info">
      <span>临促晚会照片</span>
    </div>
    <div class="info">
      <img :src="url+targetText.PROMPT_NIGHT_PICTURE"
           alt="">
    </div>
    <div class="info">
      <span>产业挂靠人是否到位</span>
      <span>{{
        targetText.INDUSTRY_CALLER_IN}}</span>
    </div>
    <div class="info">
      <span>服务商挂靠人到位几人</span>
      <span>{{targetText.SERVICE_PROVIDER_CALLER_NUMBER}}</span>
    </div>
    <div class="info">
      <span>日清是否输出</span>
      <span>{{targetText.IF_OUTPUT_NISSIN}}</span>
    </div>
    <div class="info">
      <span>朋友圈转发</span>
      <span>{{targetText.MEETING_FRIEND_SEND}}</span>
    </div>

  </div>
</template>

<script>

import vinput from '@/components/vinput'
import request from '../../utils/request'
export default {
  props: ['target'],
  data () {
    return {
      target: {},
      url: 'https://www.gz-wnkj.com:8806'
    }
  },
  componts: {
    vinput
  },
  onLoad (option) {
    let url = '/atvtport/activityinfo/findByRSAtvtID.do'
    if (option.repID) {

    }
    request.request(url, 'POST', option)
      .then(res => {
        this.target = res.data.data[0]
      })
  },
  computed: {
    targetText () {
      const defaultText = {
        'REGION_ID': 'D40ABFE70E1F44AD82AC5D811B675195',
        'EVENT_HOLDER_NUMBER': 'w',
        'COLOR_TV_TARGET': '6',
        'TALLY_OWNER_TELEPHONE': '1235',
        'BLASTING_START_TIME': '2019-10-05',
        'CASADI_OVERALL_TARGET': '3',
        'SERVICE_PROVIDER_ID': '720EA911D73046128E5E8254785178BE',
        'AIR_CONDITIONING_TARGET': '8',
        'TALLY_CHANNEL': '战略联盟',
        'SERVICE_PROVIDER_NAME': '无厘头服务商',
        'EVENT_HOLDER_INDUSTRY': 'dgh',
        'STORE_NAME': 'asd',
        'ACTIVITY_TYPE': 'aqwef',
        'BLASTING_END_TIME': '2019-10-06',
        'WASHING_MACHINE_TARGET': '34',
        'REFRIGERATOR_TARGET': '6',
        'STORE_TYPE': '乡镇',
        'TALLY_OWNER_NAME': 'wgtfe',
        'EVENT_HOLDER_NAME': 'waefgv',
        'EVENT_HOLDER_TELEPHONE': '2135',
        'CLEAN_WATER_TARGET': '4',
        'ACTIVITY_OVERALL_TARGET': '2',
        'STORE_OWNER_NAME': 'asd',
        'REPRESENTATIVE_ID': '',
        'TALLY_CODE': 'df',
        'WATER_HEATER_TARGET': '34',
        'KITCHEN_APPLIANCE_TARGET': '2',
        'STORE_OWNER_TELEPHONE': '123',
        'ACTIVITY_ID': 'F252D780E844DDE81E18E92E9AF04D3',
        'REPRESENTATIVE_NAME': '',
        'REGION': '汕尾网格',
        'ACTIVITY_THEME': '一月大降价',
        'STORE_CODE': 'asd',
        'TALLY_NAME': '124',
        'ACTIVITYINFO_ID': '1decb659c7e241d0b1cbafab15108ab4',
        'FREEZER_TARGET': '7',
        'COMMERCIAL_SPACE_TARGET': '9'
      }
      return Object.assign(defaultText, this.target || {})
    }
  }
}
</script>

<style lang="scss" scoped>
.info {
  border-bottom: 1px solid #ececec;
  width: 96%;
  position: relative;
  margin-left: 4%;
  display: flex;
  height: 60rpx;
  line-height: 60rpx;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  span:nth-of-type(2) {
    padding-right: 20rpx;
  }
}
.save {
  height: 100rpx;
  position: relative;
  button {
    position: absolute;
    right: 0;
    width: 200rpx;
    height: 100rpx;
    border-radius: 0;
    line-height: 100rpx;
    color: #fff;
    background-color: rgba(255, 105, 26, 1);
  }
}
</style>

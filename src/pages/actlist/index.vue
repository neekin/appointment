<template>
  <div>
    <div class="btitle">
      <img src="/static/images/point.png">
      区域 : {{sss.REGION}} 服务商 : {{sss.SERVICE_PROVIDER_NAME}} </div>
    <div class="title">活动列表</div>

    <actitem v-for='(target,index) in targets'
             :key=index
             :target=target />
  </div>
</template>

<script>
import actitem from '@/components/actitem'
import request from '../../utils/request'
export default {
  data () {
    return {
      sss: [],
      targets: [{
        'ACTIVITY_NAME': '悠悠我心心相惜优惠活动',
        'CREATE_TIME': '2019-10-22 12:31:22',
        'ACTIVITY_ID': '383A9C9E20F84B29B70C27A011D19F18'
      },
      {
        'ACTIVITY_NAME': '这次第',
        'CREATE_TIME': '2019-09-14 12:30:59',
        'ACTIVITY_ID': '6E3BB88E4874447E9402AA9B37C2FAE2'
      },
      {
        'ACTIVITY_NAME': '凄凄惨惨戚戚',
        'CREATE_TIME': '2019-10-31 12:30:59',
        'ACTIVITY_ID': 'AE791AF6379F415286FCD144DF78FA88'
      },
      {
        'ACTIVITY_NAME': '寻寻觅觅',
        'CREATE_TIME': '2019-10-31 12:30:59',
        'ACTIVITY_ID': '6AFEE14EE5954B4A99559D03DE850FFC'
      },
      {
        'ACTIVITY_NAME': '冷冷清清',
        'CREATE_TIME': '2019-09-10 21:08:36',
        'ACTIVITY_ID': 'DCB2855C07E14BA185ECAB84220E4A42'
      },
      {
        'ACTIVITY_NAME': '怎一个愁字了得',
        'CREATE_TIME': '2019-09-18 21:09:07',
        'ACTIVITY_ID': '6709935C192344D48A0BB9DBB0DF512E'
      }]

    }
  },
  components: {
    actitem
  },
  onLoad (option) {
    this.sss = {}
    // this.targets = []
    let url = '/atvtport/activityinfo/findTaskBySerId.do'
    if (!option.serID) {
      url = '/atvtport/activityinfo/findTaskByRepId.do'
    }
    request.request(url, 'POST', option)
      .then(res => {
        this.targets = res.data.data
        this.sss = this.targets[0]
      })
  }
}
</script>

<style lang="scss" scoped>
</style>

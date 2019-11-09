<template>
  <div>
    <div class="title">
      活动准备阶段
    </div>
    <ul v-if='list.length'>
      <!-- <li>
        <p>活动物料系统企划完成，广告公司拉入活动群</p>
        <p>xxxxxxx</p>
      </li>
      <li>
        <p>活动临促招聘启动</p>
        <p>xxxxxxx</p>
      </li>
      <li>
        <p>活动物料定稿</p>
        <p>xxxxxxx</p>
      </li>
      <li>
        <p>物料到店</p>
        <p>xxxxxxxx</p>
      </li> -->
      <li v-for='(item,index) in list'
          :key=index>
        <p>{{item.CONTENT}}</p>
      </li>
    </ul>
    <div v-else>
      没有相关数据
    </div>
  </div>
</template>

<script>
import request from '../../utils/request'
export default {
  data () {
    return {
      list: []
    }
  },
  onLoad (option) {
    console.log(option)
    request.request('/atvtport/activityStage/findStageByAtvtID.do', 'POST', option)
      .then(res => {
        this.list = res.data.data
      })
  }
}
</script>

<style lang="scss" scoped>
p {
  font-size: 12px;
}
li p:nth-of-type(1) {
  line-height: 60rpx;
}
li p:nth-of-type(2) {
  line-height: 80rpx;
}
li {
  border-bottom: 1px solid #ccc;
  width: 96%;
  margin: 0 auto;
}
</style>

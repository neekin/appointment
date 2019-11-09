<template>
  <div>
    <div class="btitle">
      <img src="/static/images/point.png">
      区域 :{{regionName}} </div>
    <div class="title">网格总监</div>
    <infoitem :target="region" />
    <tab :items='items'
         :active='activeId'
         @changeActive='change'></tab>
    <infolist v-for='(ser,index) in list'
              :target="ser"
              :key=index
              @childClick='gotolist($event)' />
  </div>
</template>

<script>
import infoitem from '@/components/infoitem'
import tab from '@/components/tab'
import infolist from '@/components/infolist'
import request from '../../utils/request'
export default {
  components: {
    infoitem,
    tab,
    infolist
  },
  data () {
    return {
      activeId: 1,
      items: [{ id: 1, value: '服务商' }, { id: 2, value: '代表' }],
      serlist: [],
      replist: [],
      list: null,
      regionName: '',
      region: null
    }
  },
  methods: {
    change (id) {
      this.activeId = id
      if (id === 1) {
        this.list = this.serlist
      } else {
        this.list = this.replist
      }
    },
    gotolist (obj) {
      // console.log(obj)
      let url = '/pages/actlist/main'
      if (obj.serID) {
        url += '?serID=' + obj.serID
        url += '&region_id=' + obj.region_id
      } else {
        url += '?repID=' + obj.repID
        url += '&region_id=' + obj.region_id
      }
      // console.log(url)
      wx.navigateTo({ url })
    }
  },
  onLoad (option) {
    this.regionName = ''
    this.list = null
    this.replist = null
    this.serlist = null
    request.request('/atvtport/dimensiondatainfo/loadRegionSerAndRep.do', 'POST', {
      region_id: option.id
    }).then(res => {
      this.replist = res.data.data.repList
      this.list = this.serlist = res.data.data.serList
      this.region = res.data.data.griddirector
      this.regionName = res.data.data.griddirector.region
    })
  }
}
</script>

<style lang="scss" scoped>
</style>

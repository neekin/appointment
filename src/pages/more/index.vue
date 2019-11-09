<template>
  <div>
    <div class="title">产品维度</div>
    <listitem v-for="(target,index) in targets"
              :key=index
              :target=target />
  </div>
</template>

<script>
import listitem from '@/components/listitem'
import request from '../../utils/request'
export default {
  data () {
    return {

      targets: []
    }
  },
  components: {
    listitem
  },
  onShow () {
    request.request('/atvtport/dimensiondatainfo/loadProduct.do', 'POST', {}).then(res => {
      this.targets = res.data.data.map(e => {
        e.name = e.industry
        return e
      })
    })
  }
}
</script>

<style lang="scss" scoped>
</style>

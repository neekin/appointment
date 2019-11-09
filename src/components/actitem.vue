<template>
  <div class='listitem'
       @click="$emit('childClick',targetText.ACTIVITY_ID)">
    <ul>
      <li>{{targetText.ACTIVITY_NAME}}</li>
      <li>日期： {{targetText.CREATE_TIME}}</li>
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
  methods: {
    actinfo () {
      let url = '/pages/actinfo/main?region_id=' +
        this.targetText.REGION_ID + '&activity_id=' + this.targetText.ACTIVITY_ID
      if (this.targetText.SERVICE_PROVIDER_ID) {
        url += '&serID=' + this.targetText.SERVICE_PROVIDER_ID
      } else {
        url += '&repID=' + this.targetText.REPRESENTATIVE_ID
      }
      wx.navigateTo({ url: url })
    },
    actredey () {
      wx.navigateTo({ url: '/pages/readey/main?activity_id=' + this.targetText.ACTIVITY_ID })
    },
    actdown () { wx.navigateTo({ url: '/pages/down/main?activity_id=' + this.targetText.ACTIVITY_ID }) }
  },
  computed: {
    targetText () {
      const defaultText = {
        id: 0,
        ACTIVITY_ID: '',
        ACTIVITY_THEME: '',
        ACTIVITY_TYPE: '',
        REGION: '',
        REGION_ID: '',
        SERVICE_PROVIDER_ID: '',
        SERVICE_PROVIDER_NAME: '',
        STORE_OWNER_NAME: '',
        STORE_OWNER_TELEPHONE: ''
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
    li {
      font-size: 24rpx;
      width: 50%;
    }
    li:nth-of-type(2) {
      text-align: left;
    }
    // li:nth-of-type(1) {
    //   font-weight: 900;
    //   color: #000;
    //   flex: 0 0 66.6666%;
    // }
    // li:nth-of-type(2),
    // li:nth-of-type(9),
    // li:nth-of-type(11) {
    //   color: #f00;
    // }
    // li {
    //   width: 33.333333%;
    //   height: 54rpx;
    //   line-height: 54rpx;
    //   text-align: center;
    //   list-style: none;
    //   flex: 0 0 33.3333%;
    //   font-size: 14px;
    //   box-sizing: border-box;
    //   color: #6c6c6c;
    // }
    // li:nth-of-type(4),
    // li:nth-of-type(5),
    // li:nth-of-type(6),
    // li:nth-of-type(7),
    // li:nth-of-type(8),
    // li:nth-of-type(9),
    // li:nth-of-type(10),
    // li:nth-of-type(11),
    // li:nth-of-type(12) {
    //   border-bottom: 1px solid #ececec;
    // }
    // li:nth-of-type(1),
    // li:nth-of-type(4),
    // li:nth-of-type(7),
    // li:nth-of-type(10) {
    //   text-align: left;
    //   padding-left: 20rpx;
    // }
  }
}
</style>

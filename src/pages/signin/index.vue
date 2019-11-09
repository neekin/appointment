<template>
  <div class='login'>

    <vinput text='手机'
            type='tel'
            v-model='telephone'></vinput>
    <vinput text='密码'
            type='password'
            v-model='password'></vinput>
    <button @click='login'>登录</button>
    <a href="/pages/signup/main">注册</a>
  </div>
</template>

<script>
import vinput from '@/components/vinput'
// const request = require('@/components/vinput')// 引用
import request from '@/utils/request'
export default {
  components: {
    vinput
  },
  data () {
    return {
      telephone: '15974192340',
      password: '15974192340'
    }
  },

  methods: {
    login () {
      console.log(this.telephone)
      if (!this.telephone) {
        wx.showToast({
          title: '手机不能为空',
          icon: 'none',
          duration: 1500
        })
        return
      }
      if (!this.password) {
        wx.showToast({
          title: '密码不能为空',
          icon: 'none',
          duration: 1500
        })
        return
      }
      let user = {
        telephone: this.telephone,
        password: this.password
      }
      request.request('/atvtport/userinfo/login.do', 'POST', user).then(res => {
        if (res.data.status === '200') {
          wx.setStorageSync('userinfo', JSON.stringify(res.data.data))
          wx.switchTab({
            url: '/pages/index/main'
          })
        } else {
          wx.showToast({
            title: res.data.msg,
            icon: 'none',
            duration: 1500
          })
        }
      })
    }
  },
  onShow () {
    try {
      var value = wx.getStorageSync('userinfo')
      if (value) {
        wx.switchTab({
          url: '/pages/index/main'
        })
      }
    } catch (e) {
    }
  }

}
</script>

<style lang="scss" scoped>
.login {
  padding-top: 100px;
  button {
    width: 80%;
    height: 68rpx;
    font-size: 32rpx;
    line-height: 68rpx;
    color: #fff;
    background-color: #06ad56;
    margin-top: 30px;
    font-weight: 300;
  }
  a {
    font-size: 28rpx;
    display: block;
    text-align: center;
    color: #9a9a9a;
    margin-top: 20px;
  }
}
</style>

<template>
  <div class='register'>
    <div class='info'>
      <span>姓名</span> <input type="text"
             placeholder="请输入姓名"
             v-model='user.username'>
    </div>
    <div class='info'>
      <span>手机</span> <input type="tel"
             placeholder="请输入号码(11位)"
             v-model='user.telephone'>
    </div>
    <div class='info'>
      <span>区域</span> <input type="text"
             placeholder="请选择区域"
             v-model='user.region'>
    </div>
    <div class='info'>
      <span>产业</span> <input type="text"
             placeholder="请选择产业"
             v-model='user.industry'>
    </div>
    <div class='info'>
      <span>负责客户</span> <input type="text"
             placeholder="请输入客户名称"
             v-model='user.customer'>
    </div>
    <div class='info'>
      <span>输入密码</span> <input type="password"
             placeholder="请输入密码"
             v-model='user.password'>
    </div>
    <div class='info'>
      <span>确认密码</span> <input type="password"
             placeholder="请再次输入密码"
             v-model='user.repassword'>
    </div>
    <div class="btns">
      <button @click='register'>注册</button>
      <a href="/pages/signin/main">使用已有账户登录</a>
    </div>

  </div>
</template>


<script>

import request from '../../utils/request'
export default {
  //
  data () {
    return {
      user: {
        username: '',
        telephone: '',
        region: '',
        industry: '',
        customer: '',
        password: '',
        repassword: ''

      }
    }
  },
  methods: {
    register () {
      if (!this.user.username || !this.user.telephone || !this.user.region || !this.user.customer || !this.user.password || !this.user.repassword) {
        wx.showToast({
          title: '请填写信息',
          icon: 'none',
          duration: 1500
        })
        return
      }
      if (this.user.password !== this.user.repassword) {
        wx.showToast({
          title: '两次密码不一致',
          icon: 'none',
          duration: 1500
        })
        return
      }
      request.request('/atvtport/userinfo/regist.do', 'POST', this.user).then(res => {
        console.log(res)
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.register {
  padding-top: 20px;
  .info:nth-of-type(1) {
    border-top: 1px solid #ececec;
  }
  .info {
    border-bottom: 1px solid #ececec;
    height: 100rpx;
    line-height: 100rpx;
    display: flex;
    span {
      display: inline-block;
      height: 100rpx;
      line-height: 100rpx;
      border-right: 1px solid #ececec;
      width: 180rpx;
      padding-left: 20rpx;
      position: relative;
      &::after {
        content: ">";
        position: absolute;
        right: 20rpx;
        font-weight: 900;
        color: #ececec;
        top: -4rpx;
      }
    }
    input {
      height: 100rpx;
      line-height: 100rpx;
      padding-left: 10rpx;
    }
  }
  .btns {
    margin-top: 20px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    button {
      width: 50%;
      margin: 0 0 0 10px;
      height: 70rpx;
      line-height: 70rpx;
      font-size: 30rpx;
      color: #fff;
      background-color: #0094ff;
      vertical-align: bottom;
    }
    a {
      color: #0094ff;
      font-size: 30rpx;
      vertical-align: bottom;
      margin: 10px 10px 0 0;
    }
  }
}
</style>

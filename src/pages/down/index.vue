<template>
  <div>
    <div class="title">
      活动落地信息
    </div>

    <div class="info">
      启动会召开
      <!-- <switch :checked="info.meeting"
              bindchange="switch1Change" /> -->
      <input type="text"
             v-model='targetText.meeting'
             placeholder="请输入内容">
    </div>
    <div class="info">
      实际招聘临促人数
      <input type="text"
             placeholder="请输入实际数量"
             v-model='targetText.recruitment_number_actual'>
    </div>
    <div class="info">
      战报输出
      <input type="text"
             placeholder="请输入"
             v-model='targetText.battle_output'>
    </div>
    <div class="info">
      会议朋友圈转发
      <picker @change="meetingFriendSend"
              :value="meeting_friend_send_index"
              :range="meeting_friend_send">
        <view class="picker">
          {{meeting_friend_send[meeting_friend_send_index]}}
        </view>
      </picker>
    </div>
    <div class="info">
      累计数认筹实际
      <input type="text"
             placeholder="请输入"
             v-model='targetText.cumulative_recognition_actual'>
    </div>
    <div class="info">
      累计数拆旧实际
      <input type="text"
             placeholder="请输入"
             v-model='targetText.cumulative_demolition_actual'>
    </div>
    <div class="info">
      累计数进村数量
      <input type="text"
             placeholder="请输入"
             v-model='targetText.cumulative_number_villages'>
    </div>
    <div class="info">
      认筹实际
      <input type="text"
             placeholder="请输入"
             v-model='targetText.recruit_actual'>
    </div>
    <div class="info">
      拆旧实际
      <input type="text"
             placeholder="请输入"
             v-model='targetText.demolition_actual'>
    </div>
    <div class="info">
      进村数量
      <input type="text"
             placeholder="请输入"
             v-model='targetText.number_villages'>
    </div>
    <div class="info">
      临促实到人数
      <input type="text"
             placeholder="请输入"
             v-model='targetText.prompt_number'>
    </div>
    <div class="info">
      临促早会照片
      <div class='btn'
           v-if='!camerashow'
           @click='showcamera("camerashow")'>
        <img src="/static/images/cam.png"
             alt="">
      </div>
      <button v-if='camerashow'
              type='primary'
              @click="takePhoto('prompt_morning_picture','camerashow')">保存图片</button>
    </div>
    <view class='pre'
          v-if='prompt_morning_picture'>
      <image style='width:100%;height:300px'
             :src="prompt_morning_picture"></image>
    </view>
    <camera v-if='camerashow || camerashow1'
            class='camera'
            device-position="back"
            flash="off"
            style="width: 100%; height: 300px;"></camera>
    <div class="info">
      临促晚会照片
      <div class='btn'
           v-if='!camerashow1'
           @click='showcamera("camerashow1")'>
        <img src="/static/images/cam.png"
             alt="">
      </div>
      <button v-if='camerashow1'
              type='primary'
              @click="takePhoto('prompt_night_picture','camerashow1')">保存图片</button>
    </div>
    <view class='pre'
          v-if='prompt_night_picture'>
      <!-- camera.wxml -->
      <image style='width:100%;height:300px'
             :src="prompt_night_picture"></image>
    </view>

    <div class="info">
      产业挂靠人是否到位
      <input type="text"
             placeholder="是否到位"
             v-model='targetText.industry_caller_in'>
    </div>
    <div class="info">
      服务商挂靠人到位几人
      <input type="text"
             placeholder="到位几人"
             v-model='targetText.if_output_nissin'>
    </div>
    <div class="info">
      日清是否输出
      <input type="text"
             placeholder="是否输出">
    </div>
    <div class="info">
      朋友圈转发
      <picker @change="friendSend"
              :value="friend_send_index"
              :range="friend_send">
        <view class="picker">
          {{friend_send[friend_send_index]}}
        </view>
      </picker>
    </div>
    <div class='save'>
      <button @click='save'>保存</button>
    </div>
  </div>
</template>

<script>
import vinput from '@/components/vinput'
import request from '../../utils/request'
// /atvtport/activityinfo/updateLandingStage.do

export default {
  data () {
    return {
      friend_send: ['活动门店人员', '服务商人员', '区域团队全员'],
      meeting_friend_send: ['活动门店人员', '服务商人员', '区域团队全员'],
      friend_send_index: 0,
      meeting_friend_send_index: 0,
      prompt_morning_picture: '',
      camerashow: false,
      camerashow1: false,
      prompt_night_picture: '',
      info: {
        'activity_id': '',
        'meeting': '0',
        'recruitment_number_actual': '0',
        'battle_output': '0',
        'meeting_friend_send': '0',
        'cumulative_recognition_actual': '0',
        'cumulative_demolition_actual': '0',
        'cumulative_number_villages': '0',
        'recruit_actual': '0',
        'demolition_actual': '0',
        'number_villages': '0',
        'prompt_number': '0',
        'prompt_morning_picture': '0',
        'prompt_night_picture': '0',
        'industry_caller_in': '0',
        'service_provider_caller_number': '0',
        'if_output_nissin': '0',
        'friend_send': '0'
      }
    }
  },
  componts: {
    vinput
  },
  onLoad (option) {
    wx.openSetting({
      success (res) {
        // res.authSetting['scope.camera']
        if (res.authSetting['scope.camera']) {
        }
      }
    })
    this.info.activity_id = option.activity_id
  },
  methods: {
    meetingFriendSend (e) {
      this.meeting_friend_send_index = e.target.value
      this.info.meeting_friend_send = this.meeting_friend_send[this.meeting_friend_send_index]
    },
    friendSend (e) {
      this.friend_send_index = e.target.value
      this.info.friend_send = this.friend_send[this.friend_send_index]
    },
    save () {
      request.request('/atvtport/activityinfo/updateLandingStage.do', 'POST', this.info)
        .then(res => {
          if (res.data.status === 200) {
            wx.navigateTo({ url: '/pages/actlist/main' })
          } else {
            wx.showToast({
              title: '提交失败',
              duration: 2000
            })
          }
        })
    },
    showcamera (field) {
      this[field] = !this[field]
    },
    takePhoto (field1, field2) {
      const ctx = wx.createCameraContext()
      ctx.takePhoto({
        quality: 'high',
        success: (res) => {
          this[field1] = res.tempImagePath
          this[field2] = !this[field2]
          this.info[field1] = wx.getFileSystemManager().readFileSync(res.tempImagePath, 'base64')
        }
      })
    }
  },
  computed: {
    targetText () {
      const defaultText = {
      }

      return Object.assign(defaultText, this.info || {})
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
  justify-content: space-between;

  input {
    height: 60rpx;
    line-height: 60rpx;
    margin-left: 10px;
    flex: 1;
  }
  button {
    border: none;
    height: 100%;
    outline: none;
    flex: 1;
    font-size: 12px;
  }
  .btn {
    border: none;
    height: 100%;
    outline: none;
    flex: 1;
    font-size: 12px;
    text-align: right;
    img {
      width: 30px;
      height: 30px;
    }
  }
  picker {
    margin-left: 20px;
    flex: 1;
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

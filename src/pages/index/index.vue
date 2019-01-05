<template>
  <div class="container">

    <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div>
    <div class="tabs">
       <i-tabs :current="current" @change="handleChange" :scroll='true'>
        <i-tab key="tab1" title="选项1">
        </i-tab>
        <i-tab key="tab2" title="选项2"></i-tab>
        <i-tab key="tab3" title="选项3"></i-tab>
        <i-tab key="tab4" title="选项3"></i-tab>
        <i-tab key="tab5" title="选项3"></i-tab>
        <i-tab key="tab6" title="选项3"></i-tab>
        <i-tab key="tab7" title="选项3"></i-tab>
        <i-tab key="tab8" title="选项3"></i-tab>
        <i-tab key="tab9" title="选项3"></i-tab>
        <i-tab key="tab10" title="选项3"></i-tab>
        <i-tab key="tab11" title="选项3"></i-tab>

      </i-tabs>
      <div v-show="current">

      </div>
    </div>
  <i-button @click="toggleLeft1" type="ghost">左边弹出1</i-button>

    <i-drawer mode="left" :visible="showLeft1" @close="toggleLeft1">
    <view class="demo-container">
        单击遮罩层关闭
    </view>
</i-drawer>
   <div style="width:100%;">
      <i-panel title="标题">
      <view style="padding: 15px;">PANEL 内容区域</view>
  </i-panel>
   </div>
    <i-button size="small" type="primary" :inline='true' :long='true' open-type="getUserInfo" lang="zh_CN" @getuserinfo="onGotUserInfo">>按钮</i-button>
  </div>
</template>

<script>
  import card from '@/components/card'

  export default {
    data() {
      return {
        motto: 'Hello World',
        userInfo: {},
        current:'',
        showLeft1:false
      }
    },

    components: {
      card
    },

    methods: {
      bindViewTap() {
        const url = '../logs/main'
        wx.navigateTo({
          url
        })
      },
      onGotUserInfo(e) {

        console.log(e)
      },
      handleChange(e){
        this.current = e.mp.detail.key
      },
      clickHandle(msg, ev) {
        console.log('clickHandle:', msg, ev)
      },
      toggleLeft1(){
        this.showLeft1 =!this.showLeft1
      }
    },

    created() {
      // 调用应用实例的方法获取全局数据
    }
  }

</script>

<style scoped>
  .userinfo {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .userinfo-avatar {
    width: 128rpx;
    height: 128rpx;
    margin: 20rpx;
    border-radius: 50%;
  }

  .userinfo-nickname {
    color: #aaa;
  }
  .demo-container{
    width: 400rpx;
    height: 300rpx;
    background-color: #fff;
    margin-left: 50%;
    
  }
  .usermotto {
    margin-top: 150px;
  }

  .form-control {
    display: block;
    padding: 0 12px;
    margin-bottom: 5px;
    border: 1px solid #ccc;
  }

  .counter {
    display: inline-block;
    margin: 10px auto;
    padding: 5px 10px;
    color: blue;
    border: 1px solid blue;
  }
  .tabs{
    width: 100%
  }

</style>

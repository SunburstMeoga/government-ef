<!-- 使用 type="home" 属性设置首页，其他页面不需要设置，默认为page；推荐使用json5，更强大，且允许注释 -->

<route lang="json5" type="home">
  {
    layout: 'default',
    style: {
      navigationBarTitleText: '首页',
      navigationStyle: 'custom'
    },
  }
  </route>
<template>
  <view class="flex flex-col justify-between items-center relative">
    <view class="w-full h-screen absolute inset-0">
      <image src="../../static/home/iPhone 13 mini_11 Pro_X (2).png"></image>
    </view>

    <view class="relative z-1 flex items-center" :style="`margin-top:${barHeight + 10}rpx; height: ${navbar + 6}rpx;`">
      首页
    </view>
    <view class="relative z-1 mt-6rpx h-110rpx w-full flex justify-center items-end mb-28rpx">
      <view class="bg-white rounded-24rpx w-680rpx h-88rpx flex justify-between items-center">
        <view class="w-112rpx h-91rpx -mt-22rpx text-slate-900 ml-21rpx">
          <image src="../../static/home/1.png" />
        </view>
        <view class="text-slate-900 ml-7rpx text-28rpx h-40rpx">
          环保相关行动正在进行中，点击查看
        </view>
        <view class="mr-22rpx w-20rpx h-24rpx -mt-22rpx">
          <image src="../../static/home/2.png"></image>
        </view>
      </view>
    </view>
    <view class="w-686rpx h-480rpx relative mx-auto mt-28rpx flex flex-col">
      <view class="w-686rpx h-480rpx absolute inset-0 rounded-24rpx overflow-hidden z-1">
        <image src="../../static/home/3.png"></image>
      </view>
      <view class="mt-29rpx mb-24rpx ml-32rpx w-140rpx h-186rpx relative z-4">
        <image src="../../static/home/guanjun.png" class="absolute inset-0" />
        <view class="w-full h-full flex flex-col items-center absolute inset-0 w-140rpx h-186rpx">
          <view class="mt-54rpx text-20rpx text-amber text-20rpx">第一名</view>
          <view class="text-20rpx text-slate-900 mb-10rpx text-24rpx">福田学校</view>
          <view class="flex justify-center w-full items-center h-24rpx">
            <view class="w-24rpx h-24rpx flex justify-center items-center">
              <image src="../../static/home/4.png" />
            </view>
            <view class="text-green-600 text-24rpx h-28rpx flex items-center">100</view>
          </view>
        </view>
      </view>
      <view class="ml-42rpx w-120rpx h-124rpx relative z-4" @click="toMall">
        <image src="../../static/home/mall.png" />
      </view>
    </view>

    <div class="border border-red-500 border-12rpx w-full -mt-78rpx h-120rpx relative z-4 mb-34rpx">
      <img src="../../static/home/5.png" class="w-full h-80rpx absolute inset-0" alt="" />
      <div class="w-full text-slate-9 text-center text-32rpx mt-88rpx mb-34rpx">
        宝安区已经开展
        <span class="text-amber">23</span>
        个减污替代修复项目
        <br />
        年降碳量达到
        <span class="text-amber">24</span>
        吨
      </div>
      <div class="flex justify-evenly items-center w-full">
        <div class="flex flex-col items-center" v-for="(item, index) in typeItems" :key="index">
          <div class="flex justify-center items-center w-88rpx h-88rpx mb-24rpx">
            <img :src="item.img" alt="" />
          </div>
          <div class="text-gray-500 text-28rpx">{{ item.title }}</div>
        </div>
      </div>
    </div>
  </view>
</template>

<script setup>
const barHeight = ref(0)
const navbar = ref(0)
const typeItems = ref([
  { title: '垃圾分类', img: '../../static/home/type1.png' },
  { title: '增值流放', img: '../../static/home/type2.png' },
  { title: '种植树木', img: '../../static/home/type3.png' },
  { title: '修复生态', img: '../../static/home/type4.png' },
  { title: '低碳活动', img: '../../static/home/type5.png' },
])
let toMall = () => {
  uni.navigateTo({
    url: '/pages/index/mall'
  })
}
onLoad(() => {
  uni.getSystemInfo({
    success: (e) => {
      let statusBar = 0 // 状态栏高度
      let customBar = 0 // 状态栏高度 + 导航栏高度
      navbar.value = 0 // 自定义标题与胶囊对齐高度

      statusBar = e.statusBarHeight
      const custom = wx.getMenuButtonBoundingClientRect()
      customBar = custom.bottom + custom.top - e.statusBarHeight

      navbar.value = (custom.top - e.statusBarHeight) * 2 + custom.height
      barHeight.value = statusBar * 2
      console.log(navbar.value, barHeight.value)
    },
  })
})
</script>

<style>
.main-title-color {
  color: #d14328;
}
</style>

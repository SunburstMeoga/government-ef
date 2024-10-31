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
  <div class="flex flex-col justify-between items-center relative">
    <div class="w-full h-screen absolute inset-0">
      <image src="../../static/home/iPhone 13 mini_11 Pro_X (2).png"></image>
    </div>

    <div class="relative z-1 flex items-center" :style="`margin-top:${barHeight + 10}rpx; height: ${navbar + 6}rpx;`">
      首页
    </div>
    <div class="relative z-1 mt-6rpx h-110rpx w-full flex justify-center items-end mb-28rpx">
      <div class="bg-white rounded-24rpx w-680rpx h-88rpx flex justify-between items-center">
        <div class="w-112rpx h-91rpx -mt-22rpx text-slate-900 ml-21rpx">
          <image src="../../static/home/1.png" />
        </div>
        <div class="text-slate-900 ml-7rpx text-28rpx h-40rpx">
          环保相关行动正在进行中，点击查看
        </div>
        <div class="mr-22rpx w-20rpx h-24rpx -mt-22rpx">
          <image src="../../static/home/2.png"></image>
        </div>
      </div>
    </div>
    <div class="w-686rpx h-480rpx relative mx-auto mt-28rpx flex flex-col" @click="toRank">
      <div class="w-686rpx h-480rpx absolute inset-0 rounded-24rpx overflow-hidden z-1">
        <image src="../../static/home/3.png"></image>
      </div>
      <div class="mt-29rpx mb-24rpx ml-32rpx w-140rpx h-186rpx relative z-4">
        <image src="../../static/home/guanjun.png" class="absolute inset-0" />
        <div class="w-full h-full flex flex-col items-center absolute inset-0 w-140rpx h-186rpx">
          <div class="mt-54rpx text-20rpx text-amber text-20rpx">第一名</div>
          <div class="text-20rpx text-slate-900 mb-10rpx text-24rpx">福田学校</div>
          <div class="flex justify-center w-full items-center h-24rpx">
            <div class="w-24rpx h-24rpx flex justify-center items-center">
              <image src="../../static/home/4.png" />
            </div>
            <div class="text-green-600 text-24rpx h-28rpx flex items-center">100</div>
          </div>
        </div>
      </div>
      <div class="ml-42rpx w-120rpx h-124rpx relative z-4" @click="toMall">
        <image src="../../static/home/mall.png" />
      </div>
    </div>

    <div class="border-12rpx w-full -mt-78rpx h-120rpx relative z-4 mb-34rpx">
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
      <div class="flex justify-evenly items-center w-full mt-60rpx mb-60rpx">
        <div class="flex flex-col items-center" v-for="(item, index) in typeItems" :key="index" @click="toRouter(item)">
          <div class="flex justify-center items-center w-88rpx h-88rpx mb-24rpx">
            <img :src="item.img" alt="" />
          </div>
          <div class="text-gray-500 text-28rpx">{{ item.title }}</div>
        </div>
      </div>
      <div class="flex justify-between items-center w-686rpx mx-auto text-emerald-5">
        <div class="flex justify-center items-center w-240rpx h-304rpx" @click="toRepair">
          <img src="../../static/home/home-left.png" alt="">
        </div>
        <div class="w-422rpx h-304rpx flex flex-col justify-between">
          <div class="w-422rpx h-144rpx card rounded-24rpx overflow-hidden flex flex-col justify-center items-center">
            <div class="text-28rpx font-medium mb-4rpx">低碳行为</div>
            <div class="text-24rpx font-medium">保护生态环境</div>

          </div>
          <div class="flex justify-between items-center w-422rpx ">
            <div @click="toLearn"
              class="flex card w-129rpx h-140rpx rounded-24rpx overflow-hidden flex flex-col justify-center items-center">
              <div class="text-24rpx font-medium mb-4rpx">学习</div>
              <div class="text-24rpx font-medium mb-4rpx">成长</div>

            </div>
            <div @click="toRole"
              class="flex card w-129rpx h-140rpx rounded-24rpx overflow-hidden flex flex-col justify-center items-center">
              <div class="text-24rpx font-medium mb-4rpx">积分</div>
              <div class="text-24rpx font-medium mb-4rpx">规则</div>
            </div>
            <div @click="toMessage"
              class="flex card w-129rpx h-140rpx rounded-24rpx overflow-hidden flex flex-col justify-center items-center">
              <div class="text-24rpx font-medium mb-4rpx">留言</div>
              <div class="text-24rpx font-medium mb-4rpx">建议</div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <wd-popup v-model="showRole" position="bottom" @close="handleClose">
      <div class="flex flex-col items-center justify-center relative">
        <div class="flex py-20rpx font-bold text-slate-9 text-32rpx">积分规则</div>
        <div class="w-686rpx text-zinc text-28rpx">
          ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容
          ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容
          ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容
          ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容
        </div>
        <div class="flex w-full absolute left-0 bottom-0 justify-center" v-if="!showQuestion">
          <div
            class="w-390rpx h-92rpx flex justify-center items-center bg-slate-9 text-green-500 rounded-24rpx text-32rpx"
            @click="handleClose">好的</div>
        </div>
      </div>
    </wd-popup>
  </div>
</template>

<script setup>

import { useMessage } from 'wot-design-uni'
const message = useMessage()
const barHeight = ref(0)
const navbar = ref(0)
const typeItems = ref([
  { title: '垃圾分类', img: '../../static/home/type1.png', url: '/pages/index/waste_sorting' },
  { title: '增值流放', img: '../../static/home/type2.png', url: '/pages/index/value_exile' },
  { title: '种植树木', img: '../../static/home/type3.png', url: null },
  { title: '修复生态', img: '../../static/home/type4.png', url: null },
  { title: '低碳活动', img: '../../static/home/type5.png', url: '/pages/index/low_carbon' },
])
let showRole = ref(false)
let handleClose = () => {
  showRole.value = false
}
let toLearn = () => {
  uni.navigateTo({
    url: '/pages/index/learning_growth'
  })
}
let toRole = () => {
  showRole.value = !showRole.value
}
let toMessage = () => {
  uni.navigateTo({
    url: '/pages/index/add_message'
  })
}
let toRepair = () => {
  uni.navigateTo({
    url: '/pages/index/instead_repair'
  })
}
let toRouter = (item) => {
  if (!item.url) {
    message.alert({
      msg: '正在开发，敬请期待',
      title: '提示',
      confirmButtonText: '好的'
    })
    return
  }
  console.log(item.url)
  uni.navigateTo({
    url: item.url
  })
  // if (index === 0) {
  //   uni.navigateTo({
  //     url: '/pages/home/waste_sorting'
  //   })
  // } else if (index === 1) {
  //   uni.navigateTo({
  //     url: '/pages/home/value_exile'
  //   })
  // } else if (index === 4) {
  //   uni.navigateTo({
  //     url: '/pages/home/value_exile'
  //   })
  // }
}
let toMall = () => {
  uni.navigateTo({
    url: '/pages/index/mall'
  })
}
let toRank = () => {
  uni.navigateTo({
    url: '/pages/index/rank'
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

.card {
  background: rgb(204, 238, 250);
  background: linear-gradient(180deg, rgba(204, 238, 250, 1) 0%, rgba(210, 255, 241, 1) 100%);
}
</style>

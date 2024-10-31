<route lang="json5">
{
  style: {
    navigationBarTitleText: '我的',
  },
}
</route>

<template>
  <div>
    <div class="flex w-full flex-col justify-start items-center">
      <div class="w-full h-208rpx relative flex flex-col items-center justify-center">
        <div class="absolute inset-0 -z-1">
          <img src="../../static/home/my.png" alt="">
        </div>
        <div class="w-686rpx flex justify-start h-208 items-center">
          <div class="flex w-128rpx h-128rpx rounded-full overflow-hidden mr-24rpx">
            <img src="../../static/home/avatar.png" class="w-full h-full" alt="">
          </div>
          <div class="flex h-120rpx flex-col items-start justify-center">
            <div class="text-slate-9 font-medium text-40rpx mb-16rpx">福田学校2024级1班</div>
            <div class="flex justify-start items-center text-28rpx">
              <div class="bg-green-1 text-green-3 p-4rpx px-4rpx mr-16rpx rounded-4rpx">机构用户</div>
              <div class="text-zinc-5">134 8778 8994</div>
            </div>
          </div>
        </div>
      </div>
      <div class="flex w-686rpx h-200rpx justify-center items-center">
        <img src="../../static/home/userrank.png" alt="">
      </div>
      <div class="w-600rpx flex flex-col justify-start items-center">
        <div class="flex justify-start text-zinc-7 text-28rpx h-96rpx w-full items-center"
          @click="handleOperating(item)"
          :style="index === personalOperatingItems.length - 1 ? '' : 'border-bottom:1px solid #f4f4f5'"
          v-for="(item, index) in personalOperatingItems" :key="index">
          {{ item.title }}
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
// 获取屏幕边界到安全区域距离
import { useMessage } from 'wot-design-uni';
const { safeAreaInsets } = uni.getSystemInfoSync()
const message = useMessage()
let personalOperatingItems = ref([
  { title: '机构用户管理', url: '/pages/about/user_manager' },
  { title: '机构用户排名', url: '' },
  { title: '留言反馈', url: '' },
  { title: '隐私协议', url: '' },
  { title: '退出账号', url: '' },
])

let handleOperating = (item: any) => {
  // uni.navigateTo({
  //   url: item.url
  // })
  message.alert({
    msg: '正在开发，敬请期待',
    title: '提示',
    confirmButtonText: '好的'
  })
  return
}
</script>

<style lang="scss" scoped>
.test-css {
  // mt-4=>1rem=>16px;
  margin-top: 16px;
}
</style>

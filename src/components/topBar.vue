<route lang="json5">
{
  style: {
    navigationBarTitleText: '关于',
  },
}
</route>
<template>
  <view class="mt-200rpx">this is top bar</view>
</template>

<script setup>
const { safeAreaInsets, statusBarHeight } = uni.getSystemInfoSync()

onLoad(() => {
  uni.getSystemInfo({
    success: (e) => {
      let statusBar = 0 // 状态栏高度
      let customBar = 0 // 状态栏高度 + 导航栏高度
      let navbar = 0 // 自定义标题与胶囊对齐高度

      statusBar = e.statusBarHeight
      const custom = wx.getMenuButtonBoundingClientRect()
      customBar = custom.bottom + custom.top - e.statusBarHeight

      navbar = (custom.top - e.statusBarHeight) * 2 + custom.height
      //   console.log(statusBar, customBar, navbar)
      //   barHeight.value = navbar + safeAreaInsets.top
      //   console.log(barHeight.value)
      console.log(safeAreaInsets, statusBarHeight)
    },
  })
})
</script>

<style lang="scss" scoped></style>

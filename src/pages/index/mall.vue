<route lang="json5">
    {
      style: {
        navigationBarTitleText: '积分商城',
      },
    }
    </route>

<template>
    <div class="flex flex-col justify-between items-center relative min-h-screen">
        <!-- <div class="test fixed left-0" :style="`border:1px solid red; top:${barHeight}rpx; height: ${navbar + 6}rpx;`">
            fasljdflskdfjkl</div> -->
        <div @click="toExchangeRecord"
            class="absolute right-0 top-160rpx text-zinc-4 bg-white text-24rpx rounded-l-57rpx w-124rpx h-57rpx z-3 flex justify-center items-center">
            兑换记录</div>
        <div class="w-full min-h-screen fixed inset-0 -z-1">
            <image src="../../static/home/record-banner.png"></image>
        </div>

        <div class="flex h-246rpx w-686rpx relative z-1 mt-20rpx mb-52rpx">
            <div class="flex w-full h-246rpx flex-col items-start justify-end">
                <div class="flex items-center justify-start mb-16rpx ml-32rpx">
                    <div class="text-40rpx text-slate-9 mr-16rpx">减碳积分</div>
                    <div class="text-56rpx text-green-600">3569</div>
                </div>
                <div class="flex mb-44rpx text-zinc-4 text-24rpx ml-32rpx">
                    通过减碳、规范操作、学习、留言建议都可以或许积分哦
                </div>
            </div>

            <div class="w-full absolute inset-0 -z-1">
                <img src="../../static/home/record.png" alt="" />
            </div>
        </div>

        <div class="w-686rpx flex flex-wrap justify-between pb-200rpx">
            <div class="w-329rpx mb-28rpx" v-for="(item, index) in 10" :key="index" @click="toDetails">
                <Product />
            </div>
        </div>
    </div>
</template>

<script setup>
import Product from './components/product.vue'
const barHeight = ref(0)
const navbar = ref(0)
let toExchangeRecord = () => {
    uni.navigateTo({
        url: '/pages/index/exchange_record'
    })
}
let toDetails = () => {
    uni.navigateTo({
        url: '/pages/index/product_details'
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
            barHeight.value = customBar - 16
            // barHeight.value = statusBar
            console.log(navbar.value, barHeight.value)
        },
    })
})
</script>

<style scoped></style>

<route lang="json5" type="home">
    {
      layout: 'default',
      style: {
        navigationBarTitleText: '增值流放详情',
      },
    }
    </route>
<template>
    <div class="flex flex-col justify-start items-center bg-gray-1">
        <div class="h-750rpx w-full">
            <swiper interval="300" circular indicator-dots="true" indicator-active-color="#fff" indicator-color="#ccc"
                :current="currentProduct" @change="onChange">
                <swiper-item v-for="(item, index) in pictureItems" :key="index"
                    class="flex flex-col justify-start items-center">
                    <div class="h-750rpx w-full">
                        <img :src="item" alt="">
                    </div>
                </swiper-item>
            </swiper>
        </div>
        <div class="flex w-full justify-center items-center min-h-167rpx bg-white mb-8rpx">
            <div class="flex w-686rpx flex-col justify-center items-start">
                <div class="text-slate-9 text-36rpx font-medium mb-16rpx">这里是任务名称</div>
                <div class="flex justify-start items-center ">
                    <div class="flex ml-16rpx text-emerald text-24rpx"> 已领取 </div>
                </div>
            </div>
        </div>
        <div class="flex bg-white w-full flex-col justify-start items-center pb-320rpx pt-50rpx">
            <div class="flex w-686rpx text-slate-9  text-32rpx font-medium mb-24rpx justify-start">
                <div class="w-32rpx h-32rpx mr-rpx">
                    <img src="../../static/home/4.png" alt="">
                </div>
                <div>活动详情</div>
            </div>
            <div class="flex w-686rpx text-zinc-5 mb-32rpx">
                活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明活动详情说明
            </div>
            <div class="flex w-686rpx text-slate-9  text-32rpx font-medium mb-24rpx justify-start">
                <div class="w-32rpx h-32rpx mr-rpx">
                    <img src="../../static/home/4.png" alt="">
                </div>
                <div>完成照片</div>
            </div>
            <div class="flex w-686rpx flex-col items-center justify-start">
                <div class="rounded-24rpx mb-26rpx w-full overflow-hidden w-686rpx h-472rpx"
                    v-for="(item, index) in pictureItems" :key="index">
                    <img :src="item" alt="">
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { Divider, InputNumber } from 'wot-design-uni'

const barHeight = ref(0)
const navbar = ref(0)
let currentProduct = ref(0)
let productCount = ref(0)
let productCountChange = ({ value }) => {
    console.log(value)
}
let pictureItems = [
    '../../static/home/product-details.png',
    '../../static/home/product-details.png',
    '../../static/home/product-details.png',
    '../../static/home/product-details.png',
    '../../static/home/product-details.png'
]
let onChange = (e) => { //问题发生变化
    console.log(e)
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
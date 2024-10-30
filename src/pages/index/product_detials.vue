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
                <div class="text-slate-9 text-36rpx font-medium mb-16rpx">这里是换购商品标题这里是换购商品标题这里是换购商品标题</div>
                <div class="flex justify-start items-center ">
                    <div class="flex justify-start items-center">
                        <div class="flex w-24rpx h-24rpx">
                            <img src="../../../static/home/coin.png" alt="">
                        </div>
                        <div class="text-orange text-32rpx font-bold ml-6rpx">50</div>
                    </div>
                    <div class="flex ml-16rpx text-gray-4 text-24rpx">仅剩10份</div>
                </div>
            </div>
        </div>
        <div class="flex bg-white w-full flex-col justify-start items-center pb-320rpx">
            <div class="flex justify-center items-center h-93rpx w-full">
                <wd-divider>商品详情</wd-divider>
            </div>
            <div class="flex w-full mb-24rpx h-750rpx">
                <img src="../../static/home/product-details.png" alt="">
            </div>
            <div class="flex w-686rpx text-zinc-5 mb-80rpx">
                商品详情，商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情商品详情
            </div>
            <div class="flex w-686rpx text-slate-9  text-32rpx font-medium mb-24rpx ">
                兑换说明
            </div>
            <div class="flex w-686rpx text-zinc-5">
                兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明兑换说明
            </div>
        </div>
        <div class="w-full h-296rpx fixed bottom-0 flex flex-col items-center justify-start bg-white">
            <div class="w-full h-1rpx bg-zinc-1"></div>
            <div class="flex w-686rpx h-96rpx items-center justify-between">
                <div class="flex justify-start items-center ">
                    <div class="flex justify-start items-center">
                        <div class="flex w-24rpx h-24rpx">
                            <img src="../../../static/home/coin.png" alt="">
                        </div>
                        <div class="text-orange text-32rpx font-bold ml-6rpx">50</div>
                    </div>
                    <!-- <div class="flex ml-16rpx text-gray-4">仅剩10份</div> -->
                </div>
                <div class="h-40rpx flex justify-center items-center">
                    <wd-input-number :min="3" :max="10" v-model="productCount" @change="productCountChange" />
                </div>
            </div>
            <div class="w-full h-1rpx bg-zinc-1 mb-24rpx"></div>
            <div
                class="flex justify-center items-center w-686rpx h-88rpx rounded-16rpx text-white text-28rpx bg-orange">
                立即兑换</div>
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
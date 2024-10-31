<route lang="json5">
    {
      style: {
        navigationBarTitleText: '垃圾分类',
      },
    }
    </route>
<template>
    <div class="flex flex-col justify-start items-center min-h-screen">
        <div class="flex w-full h-800rpx flex justify-center items-center">用户提供图片</div>
        <div class="relative w-full w-full h-1111rpx">
            <div class="flex w-full h-1111rpx absolute inset-0 -z-1">
                <img src="../../static/home/lajifenlei.png" alt="">
            </div>
            <div class="mt-334rpx w-695rpx mx-auto h-156rpx mb-32rpx relative">
                <div class="w-full h-full absolute inset-0 flex justify-between items-center z-1">
                    <div @click="handleTo(index)" class="flex-1 h-full" v-for="(item, index) in 4" :key="index">
                    </div>
                </div>
                <img src="../../static/home/type.png" alt="">
            </div>
            <div class="w-695rpx mx-auto h-392rpx mb-32rpx relative ">
                <div class="absolute w-56rpx h-50rpx  top-0 right-0 z-10" @click="toRank"></div>
                <img src="../../static/home/rank-top-3.png" alt="" @click="toList">
            </div>
        </div>
    </div>
</template>

<script setup>
import { Divider, InputNumber, useMessage } from 'wot-design-uni'
const message = useMessage()

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
let toList = () => {
    uni.navigateTo({
        url: '/pages/index/carbon_details'
    })
}
let handleTo = (index) => {
    if (index === 0) {
        message.alert({
            msg: '提醒',
            title: '正在开发，敬请期待',
            confirmButtonText: '好的'
        })
            .then(() => {
                console.log('点击了确定按钮')
            })
    } else if (index === 1) {
        uni.navigateTo({
            url: '/pages/index/cabin_distribution'
        })
    } else {
        message.alert({
            msg: '提醒',
            title: '正在开发，敬请期待',
            confirmButtonText: '好的'
        })
            .then(() => {
                console.log('点击了确定按钮')
            })
    }
}
let toRank = () => {
    uni.navigateTo({
        url: '/pages/index/carbon_rank'
    })
}
let handleSubmit = () => {
    message.alert({
        msg: '已成功提交',
        title: '成功',
        confirmButtonText: '好的'
    })
        .then(() => {
            console.log('点击了确定按钮')
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
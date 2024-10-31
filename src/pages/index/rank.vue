<route lang="json5">
    {
      layout: 'default',
      style: {
        navigationBarTitleText: '积分排名',
        navigationStyle: 'custom'
      },
    }
    </route>
<template>
    <div class="">
        <div class="flex flex-col items-center relative h-586rpx">
            <div class="w-full h-586rpx absolute inset-0">
                <img src="../../static/home/rank-bg.png" alt="" />
            </div>
            <div class="absolute w-492rpx h-492rpx -top-12rpx -right-68rpx z-1">
                <img src="../../static/home/earth.png" alt="" />
            </div>
            <div class="relative z-1 flex justify-center items-center w-full"
                :style="`margin-top:${barHeight + 10}rpx; height: ${navbar + 6}rpx;`">
                <div class="flex">积分排名</div>
                <div class="absolute left-34rpx top-0 w-18rpx h-36rpx" @click="goBack">
                    <img src="../../static/home/return.png" alt="" />
                </div>
            </div>
        </div>
        <div class="flex flex-col justify-start items-center w-full -mt-370rpx relative z-2 rounded-t-24rpx">
            <div class="flex w-full justify-between mb-50rpx items-center">
                <div class="flex p-8rpx rounded-12rpx ml-32rpx" style="border: 1px solid #fff">
                    <div @click="handleType(item)" class="flex px-20rpx py-8rpx text-28rpx rounded-12rpx"
                        :class="currentFilter === item.id ? 'bg-white text-black' : 'text-gray-500'"
                        v-for="(item, index) in filterItems" :key="index">
                        {{ item.title }}
                    </div>
                </div>
                <div @click="toRecord"
                    class="flex w-124rpx h-57rpx rounded-l-58rpx bg-white opacity-60 text-zinc-400 rounded-l-60rpx justify-center items-center text-24rpx">
                    积分记录</div>

            </div>
            <div class="rounded-t-24rpx bg-white w-full flex flex-col items-center justify-start mb-22rpx">
                <div class="flex justify-between items-start w-694rpx mt-60rpx">
                    <div class="flex justify-center items-center" :class="item.style"
                        v-for="(item, index) in rankTopThree.slice(0, 3)" :key="index">
                        <img :src="item.img" alt="" />
                    </div>
                </div>
            </div>
            <div class="w-686rpx">
                <div v-for="(item, index) in rankTopThree.slice(-7)" :key="index"
                    class="flex w-full justify-between items-center h-94rpx rounded-12rpx rank-bg mb-15rpx">
                    <div class="flex justify-start items-center ml-26rpx">
                        <div class="text-gray-300 mr-16rpx text-28rpx">
                            {{ index + 3 <= 9 ? `0${index + 3}` : index + 3 }} </div>
                                <div class="text-slate-900 text-32rpx">{{ item.name }}</div>
                        </div>
                        <div class="text-40rpx text-slate-900 font-bold mr-28rpx">{{ item.rank }}</div>
                    </div>
                </div>
            </div>
        </div>
</template>

<script setup>
const filterItems = ref([
    { id: 1, title: '月度榜' },
    { id: 2, title: '总榜' },
])
const rankTopThree = ref([
    { img: '../../static/home/guanjun.png', style: 'w-196rpx h-261rpx mt-24rpx' },
    { img: '../../static/home/yajun.png', style: 'w-206rpx h-274rpx' },
    { img: '../../static/home/jijun.png', style: 'w-196rpx h-261rpx mt-24rpx' },
    { name: '福田学校 2024级1班', rank: 100 },
    { name: '福田学校 2024级1班', rank: 100 },
    { name: '福田学校 2024级1班', rank: 100 },
    { name: '福田学校 2024级1班', rank: 100 },
    { name: '福田学校 2024级1班', rank: 100 },
    { name: '福田学校 2024级1班', rank: 100 },
    { name: '福田学校 2024级1班', rank: 100 },
])
const currentFilter = ref(1)
const handleType = (item) => {
    currentFilter.value = item.id
}
const barHeight = ref(0)
const navbar = ref(0)
let toRecord = () => {
    uni.navigateTo({
        url: '/pages/index/points_record'
    });
}
let goBack = () => {
    uni.goBack()
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

<style lang="scss" scoped>
.rank-bg {
    background: rgb(255, 255, 255);
    background: linear-gradient(90deg, rgba(255, 255, 255, 1) 0%, rgba(231, 248, 252, 1) 100%);
}
</style>

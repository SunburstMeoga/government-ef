<template>
    <div class="relative h-screen flex flex-col items-center">
        <div class="relative z-1 flex justify-center items-center w-full"
            :style="`margin-top:${barHeight + 10}rpx; height: ${navbar + 6}rpx;`">
            <div class="flex">积分记录</div>
            <div class="absolute left-34rpx top-0 w-18rpx h-36rpx">
                <img src="../../static/home/return.png" alt="" />
            </div>
        </div>
        <div class="absolute inset-0 w-full h-screen -z-1">
            <img src="../../static/home/record-banner.png" alt="">
        </div>
        <div class="flex h-246rpx w-686rpx relative z-1 mt-20rpx mb-52rpx">
            <div class="flex  w-full h-246rpx flex-col items-start justify-end">
                <div class="flex items-center justify-start mb-16rpx ml-32rpx">
                    <div class="text-40rpx text-slate-9 mr-16rpx">减碳积分</div>
                    <div class="text-56rpx text-green-600">3569</div>
                </div>
                <div class="flex mb-44rpx text-zinc-4 text-24rpx ml-32rpx">
                    通过减碳、规范操作、学习、留言建议都可以或许积分哦
                </div>

            </div>
            <div class="w-full absolute inset-0 -z-1">
                <img src="../../static/home/record.png" alt="">
            </div>
        </div>
        <div class="w-686rpx rounded-24rpx flex flex-col items-center justify-start relative z-1 bg-white pt-40rpx"
            style="border: border:1rpx solid #fff">
            <div v-for="(item, index) in recordItems" :key="index" class="mb-40rpx" @click="handleRecordItem(item)">
                <div class="flex justify-between w-646rpx h-50rpx items-center record-item rounded-12rpx py-4rpx">
                    <div class="flex justify-start items-center ml-8rpx">
                        <div class="flex justify-center items-center">
                            <img src="../../static/home/4.png" alt="">
                        </div>
                        <div class="ml-8rpx text-36rpx">202411</div>
                        <div class="ml-8rpx w-24rpx h-12rpx flex justify-center items-center">
                            <img src="../../static/home/down.png" alt="">
                        </div>
                    </div>
                    <div class="flex justify-end items-center mr-8rpx">
                        <div class="text-zinc-400 text-28rpx">收获 <span class="text-green-6">+2</span> </div>
                        <div class="text-zinc-400 text-28rpx ml-20rpx">消耗 <span class="text-orange-4">-2</span> </div>

                    </div>
                </div>
                <div v-show="item.showMore" class="flex flex-col justify-start items-center w-635rpx mt-32rpx">
                    <div class="w-full flex justify-between items-center mb-28rpx"
                        v-for="(_item, _index) in integralItems" :key="_index">
                        <div class="flex flex-col justify-start items-start h-86rpx">
                            <div class="text-slate-9 text-32rpx h-45rpx">{{ _item.title }}</div>
                            <div v-if="_item.exchange" class="text-sky-300 text-24rpx h-33rpx">超级好看的铅笔盒*3</div>
                            <div class="text-zinc-4 text-24rpx mt-4rpx">{{ _item.time }}</div>
                        </div>
                        <div class="text-slate-9 text-40rpx font-bold ">{{ _item.fra }}</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const barHeight = ref(0)
const navbar = ref(0)
let recordItems = ref([
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
    { showMore: false },
])
let integralItems = [
    { title: '减碳积分', time: '11-12 23:23', fra: '-2' },
    { title: '操作规范积分', time: '11-12 23:23', fra: '-2' },
    { title: '学习积分', time: '11-12 23:23', fra: '-2' },
    { title: '留言建议积分', time: '11-12 23:23', fra: '-2' },
    { title: '行为积分', time: '11-12 23:23', fra: '-2' },
    { title: '兑换商品', time: '11-12 23:23', fra: '-2', exchange: true },

]
let handleRecordItem = (item) => {
    item.showMore = !item.showMore
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
.record-item {
    background: rgb(255, 255, 255);
    background: linear-gradient(270deg, rgba(255, 255, 255, 1) 0%, rgba(231, 248, 252, 1) 100%);
}
</style>
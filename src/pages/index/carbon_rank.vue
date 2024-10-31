<route lang="json5">
    {
      style: {
        navigationBarTitleText: '减碳排名',
      },
    }
    </route>
<template>
    <div class="flex flex-col justify-start items-center">
        <div class="flex w-686rpx h-1596rpx mx-auto">
            <img src="../../static/home/rank-list-all.png" alt="" />
        </div>
        <div class="fixed flex bottom-0 left-0 w-full justify-evenly items-center h-204rpx bg-white">
            <div @click="handleBottomItem(item)" class="w-112rpx h-96rpx mt-17rpx"
                v-for="(item, index) in operatingTypes" :key="index">
                <img :src="item.img" alt="" />
            </div>
        </div>
    </div>
</template>

<script setup>
// import { uni } from '@dcloudio/uni-h5';

const filterItems = ref([
    { id: 1, title: '月度榜' },
    { id: 2, title: '总榜' },
])
const handleBottomItem = (item) => {
    if (!item.router) {
        message.alert({
            msg: '提醒',
            title: '正在开发，敬请期待',
            confirmButtonText: '好的'
        })
            .then(() => {
                console.log('点击了确定按钮')
            })
        return
    }
    uni.navigateTo({
        url: item.router,
    })
}
const operatingTypes = ref([
    { img: '../../static/home/bottom-1.png', router: '' },
    { img: '../../static/home/bottom-2.png', router: '/pages/index/cabin_distribution' },
    { img: '../../static/home/bottom-3.png', router: '' },
    { img: '../../static/home/bottom-4.png', router: '' },
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

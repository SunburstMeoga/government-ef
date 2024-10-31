<route lang="json5">
    {
      layout: 'default',
      style: {
        navigationBarTitleText: '答题结果'
      },
    }
    </route>
<template>
    <div class="flex flex-col justify-between items-center relative min-h-screen">
        <!-- <div class="test fixed left-0" :style="`border:1px solid red; top:${barHeight}rpx; height: ${navbar + 6}rpx;`">
            fasljdflskdfjkl</div> -->
        <div class="w-full min-h-screen fixed inset-0 -z-1">
            <image src="../../static/home/record-banner.png"></image>
        </div>

        <div class="flex w-full pt-48rpx flex-col items-center justify-start">
            <div class="flex w-686rpx items-center justify-between">
                <div class="flex flex-col justify-start items-start text-slate-9">
                    <div class="text-48rpx mb-14rpx">恭喜你获得减碳积分</div>
                    <div class="flex items-baseline">
                        共答对
                        <span class="text-60rpx mx-8rpx">4</span>
                        题
                    </div>
                </div>
                <div class="flex justify-center flex-col items-start w-180rpx h-153rpx relative text-orange mb-40rpx">
                    <img src="../../static/home/rank-num.png" class="absolute w-full h-full inset-0 -z-1" alt="" />
                    <div class="flex text-80rpx h-93rpx ml-6rpx">+0</div>
                    <div class="fle text-24rpx ml-26rpx">减碳积分</div>
                </div>
            </div>
            <div class="flex w-686rpx flex-col mb-200rpx">
                <div class="flex w-full h-76rpx relative z-1 justify-start items-center">
                    <div class="w-200rpx h-76rpx flex justify-center items-center">
                        <img src="../../static/home/analysis.png" class="w-200rpx h-76rpx" alt="" />
                    </div>
                </div>
                <div class="flex rounded-24rpx bg-white flex-col items-center justify-start -mt-38rpx pt-60rpx">
                    <div class="flex flex-col w-618rpx mb-32rpx" v-for="(item, index) in resultList" :key="index">
                        <div class="text-slate-9 font-bold mb-24rpx text-30rpx ">
                            {{ item.title }} [{{ item.judge === 0 ? '错误' : '正确' }}]
                        </div>
                        <div class="flex ml-50rpx flex-col justify-start items-center text-28rpx w-566rpx">
                            <div class="flex mb-18rpx w-full"
                                :class="_item.isError ? 'text-red' : _item.isRight ? 'text-green' : 'text-gray'"
                                v-for="(_item, _index) in item.answer" :key="_index">
                                {{ _item.title }}
                            </div>
                        </div>
                        <div class="flex text-28rpx w-566rpx ml-50rpx">解析：{{ item.analysis }}</div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
const barHeight = ref(0)
const navbar = ref(0)
const resultList = ref([
    {
        title: '01 以下哪些行为是正确的保护环境?',
        judge: 0,
        answer: [
            { title: 'A  乱丢垃圾' },
            { title: 'B  砍伐树木', isError: true },
            { title: 'C  不挂机', isRight: true },
            { title: 'A  我不知道' },
        ],
        analysis: '保护环境人人有责',
    },
    {
        title: '02 以下哪些行为是正确的保护环境?',
        judge: 1,
        answer: [
            { title: 'A  乱丢垃圾' },
            { title: 'B  砍伐树木', isError: true },
            { title: 'C  不挂机', isRight: true },
            { title: 'A  我不知道' },
        ],
        analysis: '保护环境人人有责',
    },
    {
        title: '03 以下哪些行为是正确的保护环境?',
        judge: 1,
        answer: [
            { title: 'A  乱丢垃圾' },
            { title: 'B  砍伐树木', isError: true },
            { title: 'C  不挂机', isRight: true },
            { title: 'A  我不知道' },
        ],
        analysis: '保护环境人人有责',
    },
    {
        title: '04 以下哪些行为是正确的保护环境?',
        judge: 1,
        answer: [
            { title: 'A  乱丢垃圾' },
            { title: 'B  砍伐树木', isError: true },
            { title: 'C  不挂机', isRight: true },
            { title: 'A  我不知道' },
        ],
        analysis: '保护环境人人有责',
    },
    {
        title: '05 以下哪些行为是正确的保护环境?',
        judge: 1,
        answer: [
            { title: 'A  乱丢垃圾' },
            { title: 'B  砍伐树木', isError: true },
            { title: 'C  不挂机', isRight: true },
            { title: 'A  我不知道' },
        ],
        analysis: '保护环境人人有责',
    },
])
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

<style scoped>
.custom-slide-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100%;
    padding: 20px;
}
</style>

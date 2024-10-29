<template>
    <div class="flex flex-col justify-between items-center relative min-h-screen">
        <!-- <div class="test fixed left-0" :style="`border:1px solid red; top:${barHeight}rpx; height: ${navbar + 6}rpx;`">
            fasljdflskdfjkl</div> -->
        <div class="w-full min-h-screen absolute inset-0 -z-1">
            <image src="../../static/home/learning.png"></image>
        </div>

        <div class="flex w-full pt-38rpx flex-col items-center justify-start" v-if="showQuestion">
            <div class="flex justify-start items-start  w-622rpx  relative mb-41rpx">
                <div class="absolute -z-1 inset-0 w-100rpx h-100rpx flex justify-center items-center">
                    <img src="../../static/home/question-num.png" alt="">
                </div>
                <div class="flex text-slate-9 text-72rpx font-black italic">{{ currentQue === 0 ? '01' : (currentQue + 1
            <= 9 ? '0' + (currentQue + 1) : currentQue + 1) }}</div>
                        <div class="flex text-zinc-4 mx-20rpx italic mt-18rpx">/</div>
                        <div class="flex text-zinc-4 text-40rpx font-black italic mt-15rpx">{{ questionList.length
            <= 9 ? '0' + questionList.length : questionList.length }}</div>
                        </div>

                        <div class="w-full h-779rpx mb-218rpx">
                            <swiper interval="300" circular :indicator-dots="false" :current="currentQue"
                                :autoplay="false" :loop="false" @change="onChange">
                                <swiper-item v-for="(item, index) in questionList" :key="index"
                                    class="flex flex-col justify-start items-center">
                                    <div class="text-black bg-transparent w-622rpx mx-aut0">
                                        <div class="flex w-480rpx text-slate-9 text-48rpx mb-68rpx">{{ item.title }}
                                        </div>
                                        <div @click="handleAnswerItem(_item, index)"
                                            class="flex mb-40rpx items-center justify-center w-622rpx h-114rpx rounded-24rpx text-slate-9 text-36rpx"
                                            :class="item.selectId === _item.id ? 'bg-cyan-1' : 'bg-white'"
                                            style="border: 1rpx solid #ecfeff"
                                            v-for="(_item, _index) in item.answerItems" :key="_index">{{ _item.title }}
                                        </div>
                                    </div>
                                </swiper-item>
                            </swiper>
                        </div>

                        <div class="text-slate-9 text-32rpx flex justify-between items-center w-312rpx mx-auto">
                            <div @click="handlePreQue()">上一题</div>

                            <div :class="currentQue === questionList.length - 1 ? 'text-amber' : ''"
                                @click="handleNextQue()">{{ currentQue === questionList.length - 1 ? '提交答案' : '下一题' }}
                            </div>
                        </div>
                </div>

                <div class="flex w-full fixed bottom-136rpx justify-center" v-if="!showQuestion">
                    <div class="w-390rpx h-92rpx flex justify-center items-center bg-slate-9 text-green-500 rounded-24rpx text-32rpx"
                        @click="handleTest()">立即测试</div>
                </div>
                <!-- <wd-message-box /> -->

            </div>
</template>

<script setup>
const barHeight = ref(0)
const navbar = ref(0)
let currentQue = ref(0) //当前问题
import { useMessage } from 'wot-design-uni'
const message = useMessage()
const questionList = ref([
    { title: '以下哪个行为是正确的保护环境', selectId: null, answerItems: [{ id: 1, title: '乱丢垃圾' }, { id: 2, title: '砍伐树木' }, { id: 3, title: '不挂机' }, { id: 4, title: '我不知道' }] },
    { title: '以下哪个行为是正确的保护环境', selectId: null, answerItems: [{ id: 5, title: '乱丢垃圾' }, { id: 6, title: '砍伐树木' }, { id: 7, title: '不挂机' }, { id: 8, title: '我不知道' }] },
    { title: '以下哪个行为是正确的保护环境', selectId: null, answerItems: [{ id: 9, title: '乱丢垃圾' }, { id: 10, title: '砍伐树木' }, { id: 11, title: '不挂机' }, { id: 12, title: '我不知道' }] },
    { title: '以下哪个行为是正确的保护环境', selectId: null, answerItems: [{ id: 13, title: '乱丢垃圾' }, { id: 14, title: '砍伐树木' }, { id: 15, title: '不挂机' }, { id: 16, title: '我不知道' }] },

])
const typeItems = ref([
    { title: '垃圾分类', img: '../../static/home/type1.png' },
    { title: '增值流放', img: '../../static/home/type2.png' },
    { title: '种植树木', img: '../../static/home/type3.png' },
    { title: '修复生态', img: '../../static/home/type4.png' },
    { title: '低碳活动', img: '../../static/home/type5.png' },
])
let handleAnswerItem = (_item, index) => {
    questionList.value[index].selectId = _item.id

}
let handleClick = (e) => { //点击问题
    console.log(e)
}
let onChange = (e) => { //问题发生变化
    console.log(e)
}
let handleNextQue = () => { //点击下一题
    currentQue.value = ++currentQue.value
    console.log(questionList.value.length - 1)

}
let handlePreQue = () => { //点击下一题
    currentQue.value = --currentQue.value
    console.log(questionList.value.length - 1)
}
let showQuestion = ref(true) //问题列表显隐
let handleTest = () => { //点击立即测试按钮
    //暂不可答题 起弹窗
    // message.alert({
    //     msg: '本周已答题并获取了积分，下次开启答题时间为下周一（00:00）',
    //     title: '暂不支持答题',
    //     confirmButtonText: '好的'
    // })
    //显示题目列表开始做题
    showQuestion.value = true
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

<style scoped>
.custom-slide-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 20px;
    height: 100%;
}
</style>
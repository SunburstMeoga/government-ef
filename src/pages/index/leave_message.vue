<route lang="json5" type="home">
    {
      style: {
        navigationBarTitleText: '留言反馈',
      },
    }
    </route>
<template>
    <div class="flex flex-col justify-start items-center bg-slate-50 min-h-screen">
        <div class="flex w-686rpx flex-col mt-32rpx">
            <div class="flex items-center h-50rpx mb-28rpx">
                <div class="mr-40rpx" v-for="(item, index) in messageTypes" @click="handleMessageType(item)"
                    :class="currentMessageType === item.id ? 'text-slate-9 font-medium text-36rpx' : 'text-gray-5 text-32rpx'"
                    :key="index">
                    {{ item.title }}(0)
                </div>
            </div>
        </div>
        <div class="flex w-full flex-col justify-start items-center mb-300rpx">
            <div class="flex w-686rpx rounded-24rpx overflow-hidden bg-white mb-28rpx" v-for="(item, index) in 10"
                :key="index">
                <Message />
            </div>
        </div>
    </div>
</template>

<script setup>
import { Message } from './components/message.vue'
const barHeight = ref(0)
const navbar = ref(1)
let messageTypes = ref([ //留言类型
    { title: '待处理', id: 1 },
    { title: '已处理', id: 2 }
])
let currentMessageType = ref(1)
let handleMessageType = (item) => {
    currentMessageType.value = item.id
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
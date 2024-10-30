<template>
    <div class="flex flex-col justify-start items-center bg-slate-50">
        <div class="flex w-686rpx flex-col mt-32rpx">
            <div class="flex rounded-24rpx  bg-white mb-28rpx min-h-217rpx" v-for="(item, index) in 10" :key="index">
                <Instead />
            </div>
        </div>
    </div>
</template>

<script setup>
import Instead from './components/instead.vue'
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
            barHeight.value = customBar - 16
            // barHeight.value = statusBar
            console.log(navbar.value, barHeight.value)
        },
    })
})
</script>

<style scoped></style>
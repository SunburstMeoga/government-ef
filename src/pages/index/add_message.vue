<route lang="json5">
    {
      layout: 'default',
      style: {
        navigationBarTitleText: '留言反馈'
      },
    }
    </route>
<template>
    <div class="flex flex-col justify-start items-center  min-h-screen relative">
        <div class="w-full h-1684rpx absolute inset-0 -z-1 ">
            <img src="../../static/home/message-banner.png
            " alt="">
        </div>
        <div class="flex w-686rpx flex-col mt-32rpx">
            <div class="flex justify-start items-center mb-13rpx">
                <div class="flex font-medium text-64rpx text-slate-9">Hello</div>
                <div class="flex justify-center items-center w-112rpx h-92rpx">
                    <img src="../../static/home/1.png" alt="">
                </div>
            </div>
            <div class="flex text-gray-5 text-32rpx mb-40rpx">请留下您的宝贵意见</div>
            <div class="rounded-24rpx bg-white p-28rpx mb-32rpx">
                <div class="flex w-full justify-between items-end mb-24rpx">
                    <div class="text-slate-9 font-medium text-36rpx">反馈内容</div>
                    <div class="text-neutral-300 text-28rpx">0/500</div>
                </div>
                <div class="w-630rpx mb-24rpx">
                    <textarea name="" id="" cols="30" rows="10" class="text-32rpx"
                        placeholder="请填写10个字以上的内容，以便我们为您提供更好的回复。（必填）"></textarea>
                </div>
                <div class="flex w-full justify-start items-end mb-24rpx">
                    <div class="text-slate-9 font-medium text-36rpx">相关图片</div>
                    <div class="text-neutral-300 text-28rpx">(仅支持3张5M以内图片)</div>
                </div>
                <div>
                    <wd-upload :file-list="fileList" :limit="3"
                        action="https://mockapi.eolink.com/zhTuw2P8c29bc981a741931bdd86eb04dc1e8fd64865cb5/upload"
                        @change="handleChange"></wd-upload>
                </div>
            </div>
            <div class="rounded-24rpx bg-white p-28rpx">
                <div class="flex w-full justify-between items-end mb-24rpx">
                    <div class="text-slate-9 font-medium text-36rpx">联系电话</div>
                </div>
                <div class="w-630rpx mb-24rpx">
                    <input placeholder="请输入常用手机号，以便结果反馈(必填)" class="text-32rpx"></input>
                </div>
            </div>
        </div>
        <div class="flex w-full h-200rpx bg-white justify-center items-start fixed bottom-0 left-0">
            <div @click="handleSubmit()"
                class="flex justify-center items-center text-emerald bg-slate-9 rounded-24rpx w-486rpx h-92rpx mt-20rpx">
                提交留言
            </div>
        </div>
    </div>
</template>

<script setup>
// import { uploadThemeVars } from 'wot-design-uni/components/wd-config-provider/types';
import { uploadThemeVars } from 'wot-design-uni';
import { useMessage } from 'wot-design-uni'
const message = useMessage()
const barHeight = ref(0)
const navbar = ref(1)
let fileList = ref([])
let handleChange = ({ files }) => {
    console.log('object :>> ', files);
}
let handleSubmit = () => {
    message.alert({
        msg: '谢谢您的留言反馈，已成功提交',
        title: '成功',
        confirmButtonText: '好的'
    })
        .then(() => {
            uni.switchTab({
                url: '/pages/index/index'
            })
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
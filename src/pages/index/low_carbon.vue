<route lang="json5">
    {
      style: {
        navigationBarTitleText: '低碳活动',
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
                <div class="flex font-medium text-36rpx text-slate-9">请选择低碳行为类型</div>
            </div>
            <div class="flex w-full justify-between items-center mb-40rpx">
                <div @click="handleType(item)"
                    class="flex justify-center items-center w-210rpx h-72rpx rounded-16rpx text-28rpx"
                    :class="selectType === item.id ? 'select-item' : 'normal-item'" v-for="(item, index) in actionTypes"
                    :key="index">{{ item.title }}</div>
            </div>
            <div class="rounded-24rpx bg-white p-28rpx mb-32rpx">

                <div class="flex w-full justify-start items-end mb-12rpx">
                    <div class="text-slate-9 font-medium text-36rpx">相关图片</div>
                    <div class="text-neutral-300 text-28rpx">(仅支持3张5M以内图片)</div>
                </div>
                <div class="mb-24rpx text-neutral-3 text-24rpx">Tips:每周仅能提交获取一次积分</div>
                <div>
                    <wd-upload :file-list="fileList" :limit="3"
                        action="https://mockapi.eolink.com/zhTuw2P8c29bc981a741931bdd86eb04dc1e8fd64865cb5/upload"
                        @change="handleChange"></wd-upload>
                </div>
            </div>
            <div class="rounded-24rpx bg-white p-28rpx text-zinc-4 text-28rpx">
                ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容 <br />
                ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容 <br />
                ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容 <br />
                ·绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容，绿色低碳班会描述内容，绿色低碳班会描述内容绿色低碳班会描述内容
            </div>
        </div>
        <div class="flex w-full h-200rpx bg-white justify-center items-start fixed bottom-0 left-0">
            <div @click="handleSubmit()"
                class="flex justify-center items-center text-emerald bg-slate-9 rounded-24rpx w-486rpx h-92rpx mt-20rpx">
                提交
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
let selectType = ref(1)
let actionTypes = ref([
    { title: '绿色低碳班会', id: 1 },
    { title: '低碳教育基地', id: 2 },
    { title: '保护生态环境', id: 3 },
])
let handleType = (item) => {
    selectType.value = item.id
}
let handleChange = ({ files }) => {
    console.log('object :>> ', files);
}
let handleSubmit = () => {
    message.alert({
        msg: '已成功提交',
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

<style scoped>
.normal-item {
    color: #52525b;
    background-color: #fff;
    border: 1px solid #fff;
}

.select-item {
    color: #0f172a;
    border: 1px solid #7ED2EF;
    background: rgb(150, 221, 246);
    background: linear-gradient(135deg, rgba(150, 221, 246, 1) 0%, rgba(231, 248, 252, 1) 21%, rgba(179, 250, 225, 1) 63%, rgba(148, 239, 184, 1) 100%);
}
</style>
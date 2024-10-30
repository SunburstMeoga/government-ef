<template>
    <div class="w-686rpx py-28rpx flex flex-col items-center">
        <div class="flex w-630rpx flex-col justify-start items-center mx-auto">
            <div class="text-slate-9 mb-20rpx text-32rpx flex justify-start items-center mb-24rpx w-full">
                <div class="flex mr-8rpx">2024/12/12</div>
                <div
                    class="text-20rpx w-76rpx h-36rpx flex justify-center items-center justify-center text-green-400 bg-green-100 border border-green-5">
                    已处理</div>
            </div>
            <div class="flex bg-slate-50 rounded-24rpx flex flex-col justify-center items-center w-630rpx py-28rpx">
                <div class="w-582rpx text-gray-5 mb-16rpx text-28rpx">关于什么问题关于什么问题关于什么问题关于什么问题关于什么问题</div>
                <div class="w-582rpx flex justify-start items-center">
                    <div :class="index === 0 ? '' : 'ml-24rpx'"
                        class="flex justify-center items-center w-120rpx h-120rpx rounded-12rpx overflow-hidden"
                        v-for="(item, index) in 4" :key="index">
                        <img src="../../static/home/product-details.png" alt="">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup></script>

<style lang="scss" scoped></style>
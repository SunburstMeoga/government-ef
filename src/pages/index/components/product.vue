<route lang="json5" type="page">
{
  layout: 'default',
  style: {
    navigationBarTitleText: '',
  },
}
</route>
<template>
    <div class="rounded-24rpx overflow-hidden bg-white">
        <div class="flex justify-center items-center h-220rpx rounded-24rpx overflow-hidden">
            <img src="../../../static/home/product.png" alt="">
        </div>
        <div class="flex h-128rpx flex-col justify-center items-center w-full">
            <div class="text-slate-9 text-28rpx font-semibold w-276rpx mb-12rpx">商品title</div>
            <div class="flex w-276rpx items-center justify-between">
                <div class="text-gray-4 text-24rpx">仅剩10份</div>
                <div class="flex items-center justify-end">
                    <div class="flex w-24rpx h-24rpx">
                        <img src="../../../static/home/coin.png" alt="">
                    </div>
                    <div class="text-orange text-32rpx font-bold ml-6rpx">50</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup></script>

<style lang="scss" scoped></style>

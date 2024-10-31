<route lang="json5" type="home">
    {
      style: {
        navigationBarTitleText: '登录',
      },
    }
    </route>
<template>
    <div class="h-screen w-full relative flex flex-col justify-center items-center">
        <div class="absolute w-full h-screen  -z-1">
            <img src="../../static/home/login.png" alt="">
        </div>
        <div @click="toHome"
            class="w-622rpx h-114rpx text-green-6 bg-slate-9 rounded-24rpx mb-48rpx flex justify-center items-center text-36rpx font-medium">
            手机号快捷登录</div>
        <div class="text-zinc-400">
            <wd-checkbox :modelValue="true" shape="square">同意《XXXX用户服务协议》《隐私协议》</wd-checkbox>
        </div>
    </div>
</template>

<script setup>
import { checkboxThemeVars } from 'wot-design-uni';
let toHome = () => {
    uni.switchTab({
        url: '/pages/index/index'
    });
}
</script>

<style lang="scss" scoped></style>
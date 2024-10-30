<route lang="json5" type="home">
    {
      layout: 'default',
      style: {
        navigationBarTitleText: '小屋分布',
      },
    }
    </route>
<template>
    <view class="container">
        <map :latitude="latitude" :longitude="longitude" :scale="16" style="width: 100%; height: 400px;"
            :markers="markers" />
    </view>
</template>

<script setup>
import { onMounted } from 'vue';

let latitude = ref(22.5865)
let longitude = ref(113.8635)
let markers = ref([{
    id: 1,
    latitude: 22.5865,
    longitude: 113.8635,
    iconPath: "../..//static/marker.png", // 标记点的图标
    width: 30,
    height: 30
}])


</script>

<style lang="scss" scoped>
.container {

    width: 100%;
    height: 100vh;
}

button {
    margin-top: 10px;
    padding: 10px;
    background-color: #007AFF;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
</style>
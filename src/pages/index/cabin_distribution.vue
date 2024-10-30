<template>
  <view class="container">
    <map
      :latitude="latitude"
      :longitude="longitude"
      :scale="16"
      style="width: 100%; height: 400px"
      :markers="markers"
    />
  </view>
</template>

<script setup>
import { onMounted } from 'vue'

const latitude = ref(22.5865)
const longitude = ref(113.8635)
const markers = ref([
  {
    id: 1,
    latitude: 22.5865,
    longitude: 113.8635,
    iconPath: '../..//static/marker.png', // 标记点的图标
    width: 30,
    height: 30,
  },
])
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100vh;
}

button {
  padding: 10px;
  margin-top: 10px;
  color: #ffffff;
  cursor: pointer;
  background-color: #007aff;
  border: none;
  border-radius: 5px;
}
</style>

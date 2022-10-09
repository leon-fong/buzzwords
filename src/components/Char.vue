<script setup lang="ts">
import mi_bg from '~/assets/mi_bg.svg'
const props = defineProps(['value'])
const bgStyle = `background-image: url(${mi_bg})`
</script>

<template>
  <div class="flex-1">
    <div class="wrap">
      <div class="flex absolute w-full h-full">
        <span class="char" :style="bgStyle">{{ props.value }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrap {
  position: relative;
}
.wrap:after {
  content: "";
  display: block;
  padding-bottom: 100%;
}
.char {
  flex: 1;
  font-size: 50px;
  justify-content: center;
  display: flex;
  align-items: center;
  font-family: '\6977\4F53', '楷体', '\6977\4F53_GB2312', '楷体_GB2312',
    '\534E\6587\6977\4F53', '华文楷体', '\6807\6977\4F53', 'KaiTi',
    'KaiTi_GB2312', 'Kaiti SC', 'STKaiti', 'AR PL UKai CN', 'AR PL UKai HK',
    'AR PL UKai TW', 'AR PL UKai TW MBE', 'AR PL KaitiM GB', 'DFKai-SB',
    'TW-Kai', 'Noto Serif SC', serif;
    /* background-image: url('./mi_bg.svg'); */
  background-size: cover;
  background-repeat: no-repeat;
}
</style>

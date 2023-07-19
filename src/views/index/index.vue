<script setup lang="ts">
import ItemWrap from '@/components/item-wrap'
import LeftTop from './left-top.vue'
import LeftCenter from './left-center.vue'
import LeftBottom from './left-bottom.vue'
import CenterMap from './center-map.vue'
import CenterBottom from './center-bottom.vue'
import RightTop from './right-top.vue'
import RightCenter from './right-center.vue'
import RightBottom from './right-bottom.vue'
import { ref } from 'vue'
const loading = ref<Boolean>(true)
setTimeout(() => {
  loading.value = false
}, 1300)
</script>

<template>
  <div v-if="loading" class="first-loading-wrp">
    <div class="loading-wrp">
      <span class="dot dot-spin">
        <i></i>
        <i></i>
        <i></i>
        <i></i>
      </span>
    </div>
    <h1>正在加载数据...</h1>
  </div>
  <div v-else class="index-box">
    <div class="contetn_left">
      <!-- <div class="pagetab">
        <div class="item">实时监测</div>
        <div class="item">统计分析</div>
      </div> -->
      <ItemWrap class="contetn_left-top contetn_lr-item" title="设备总览">
        <LeftTop />
      </ItemWrap>
      <ItemWrap class="contetn_left-center contetn_lr-item" title="用户总览">
        <LeftCenter />
      </ItemWrap>
      <ItemWrap
        class="contetn_left-bottom contetn_lr-item"
        title="设备提醒"
        style="padding: 0 10px 16px 10px"
      >
        <LeftBottom />
      </ItemWrap>
    </div>
    <div class="contetn_center">
      <CenterMap class="contetn_center_top" title="设备分布图" />
      <ItemWrap class="contetn_center-bottom" title="安装计划">
        <CenterBottom />
      </ItemWrap>
    </div>
    <div class="contetn_right">
      <ItemWrap class="contetn_left-top contetn_lr-item" title="报警次数">
        <RightTop />
      </ItemWrap>
      <ItemWrap
        class="contetn_left-center contetn_lr-item"
        title="报警排名(TOP8)"
        style="padding: 0 10px 16px 10px"
      >
        <RightCenter />
      </ItemWrap>
      <ItemWrap class="contetn_left-bottom contetn_lr-item" title="数据统计图 ">
        <RightBottom />
      </ItemWrap>
    </div>
  </div>
</template>

<style scoped lang="scss">
.first-loading-wrp {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 90vh;
  min-height: 90vh;
}

.first-loading-wrp > h1 {
  font-size: 24px;
  font-weight: bolder;
}

.first-loading-wrp .loading-wrp {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 58px;
}

.dot {
  position: relative;
  box-sizing: border-box;
  display: inline-block;
  width: 64px;
  height: 64px;
  font-size: 64px;
  transform: rotate(45deg);
  animation: antRotate 1.2s infinite linear;
}

.dot i {
  position: absolute;
  display: block;
  width: 28px;
  height: 28px;
  // background-color: #1890ff;
  background-image: linear-gradient(to right, #256ccf 0%, #2d4ed0  51%, #1f79ff  100%);
  border-radius: 100%;
  opacity: 0.3;
  transform: scale(0.75);
  transform-origin: 50% 50%;
  animation: antSpinMove 1s infinite linear alternate;
}

.dot i:nth-child(1) {
  top: 0;
  left: 0;
}

.dot i:nth-child(2) {
  top: 0;
  right: 0;
  -webkit-animation-delay: 0.4s;
  animation-delay: 0.4s;
}

.dot i:nth-child(3) {
  right: 0;
  bottom: 0;
  -webkit-animation-delay: 0.8s;
  animation-delay: 0.8s;
}

.dot i:nth-child(4) {
  bottom: 0;
  left: 0;
  -webkit-animation-delay: 1.2s;
  animation-delay: 1.2s;
}

@keyframes antRotate {
  to {
    -webkit-transform: rotate(405deg);
    transform: rotate(405deg);
  }
}

@-webkit-keyframes antRotate {
  to {
    -webkit-transform: rotate(405deg);
    transform: rotate(405deg);
  }
}

@keyframes antSpinMove {
  to {
    opacity: 1;
  }
}

@-webkit-keyframes antSpinMove {
  to {
    opacity: 1;
  }
}
.index-box {
  width: 100%;
  display: flex;
  min-height: calc(100% - 64px);
  justify-content: space-between;
}

.contetn_left {
  .contetn_left-top {
    animation: left 1.8s;
  }
  .contetn_left-center {
    animation: left 2.3s;
  }
  .contetn_left-bottom {
    animation: left 2.8s;
  }
}
@keyframes left {
  0% {
    transform: translateX(-1000px);
  }
  80% {
    transform: translateX(20px);
  }
  100% {
    transform: translateX(0);
  }
}
.contetn_center {
  .contetn_center_top {
    animation: slideAndFade 1.8s;
  }
  .contetn_center-bottom {
    animation: slideAndFades 2.5s;
  }
}
@keyframes slideAndFade {
  0% {
    transform: translateY(-200px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}
@keyframes slideAndFades {
  0% {
    transform: translateY(200px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

.contetn_right {
  .contetn_left-top {
    animation: right 1.8s;
  }
  .contetn_left-center {
    animation: right 2.3s;
  }
  .contetn_left-bottom {
    animation: right 2.8s;
  }
}

@keyframes right {
  0% {
    transform: translateX(1000px);
  }
  80% {
    transform: translateX(-20px);
  }
  100% {
    transform: translateX(0);
  }
}
//左边 右边 结构一样
.contetn_left,
.contetn_right {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  position: relative;
  width: 540px;
  box-sizing: border-box;
  flex-shrink: 0;
}
.contetn_center {
  flex: 1;
  margin: 0 54px;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  .contetn_center-bottom {
    height: 315px;
  }
}

.contetn_lr-item {
  height: 310px;
}
</style>

<template>
  <div class="sao-container">
    <transition
      :duration="500"
      mode="out-in"
      enter-active-class="animate__animated animate__fadeInDown"
      leave-active-class="animate__animated animate__fadeOutUp">
      <div class="sao-login" v-if="showType==1">
        <div class="sao-ques">你是骚包嘛 <span>?</span></div>
        <div class="sao-btn" @click="change">是</div>
        <div class="sao-btn_disabled">不是</div>
      </div>
      <div class="sao-content" v-else-if="showType==2">
        <div>骚气包</div>
        <div>骚大强生日快乐</div>
      </div>
      <div class="sao-content_3" v-else-if="showType==3">
        <div>朋友是天朋友是地</div>
        <div>有了朋友可以顶天立地</div>
        <div>朋友是雨，朋友是风</div>
        <div>有了朋友可以呼风唤雨</div>
        <div>祝骚骚强</div>
        <div>生日快乐</div>
        <div class="sao-content_img"></div>
      </div>
    </transition>
    <div class="btn-container">
      <transition
        :duration="1000"
        enter-active-class="animate__animated animate__fadeInLeft"
        leave-active-class="animate__animated animate__fadeOutLeft">
        <div v-if="showType==2">
          <div class="sao-btn" @click="change">喜欢</div>
        </div>
      </transition>
      <transition
        :duration="1000"
        enter-active-class="animate__animated animate__fadeInRight"
        leave-active-class="animate__animated animate__fadeOutRight">
        <div v-if="showType==2">
          <div class="sao-btn_disabled">不喜欢</div>
        </div>
      </transition>
    </div>
    <div v-if="showType!==1">
      <audio src="../assets/hp.mp3" autoplay loop></audio>
      <div v-for="e in 1000" :key="e" class="snow"></div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const showType = ref(1)
const change = () => {
  showType.value++
}
</script>

<!-- <style>
/* 进入之前和离开后的样式 */
.v-enter-from,
.v-leave-to {
  opacity: 0;
}
/* 离开和进入过程中的样式 */
.v-enter-active,
.v-leave-active {
  /* 添加过渡动画 */
  transition: opacity 1s ease;
}
/* 进入之后和离开之前的样式 */
.v-enter-to,
.v-leave-from {
  opacity: 1;
}
</style> -->
<style>
@keyframes zhuan {
  0% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(360deg);
  }
  100% {
    transform: rotate(720deg);
  }
}
</style>
<style lang="scss">
.sao-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background-color: #000;
  background-image: url('../assets/bgc.webp');
  background-size: 100% 100%;
  background-repeat: no-repeat;
  color: #fff;
  .sao-login {
    text-align: center;
  }
  .sao-ques {
    // text-align: center;
    font-size: 30px;
    line-height: 50px;
    margin-top: 20vh;
    span {
      display: inline-block;
      font-size: 50px;
      transform: rotate(15deg)
    }
  }
  .sao-btn {
    text-align: center;
    font-size: 20px;
    background-color: #fff;
    width: 100px;
    margin: 10px auto;
    border-radius: 5px;
    color: #ffbab2;
    cursor: pointer;
    user-select: none;
    opacity: 0.5;
  }
  .sao-btn_disabled {
    text-align: center;
    font-size: 20px;
    background-color: #fff;
    width: 100px;
    margin: 10px auto;
    border-radius: 5px;
    color: #ffbab2;
    cursor: not-allowed;
    user-select: none;
    opacity: 0.5;
  }
  .sao-content {
    text-align: center;
    font-size: 30px;
    line-height: 50px;
    margin-top: 20vh;
  }
  .btn-container {
    text-align: center;
    margin-top: 10vh;
    div {
      display: inline-block;
      & + div {
        margin-left: 10vw;
      }
    }
  }
  .sao-content_3 {
    position: relative;
    width: 50vw;
    height: 200px;
    padding: 20px;
    margin: 20vh auto;
    color: rgba(0,0,0, .85);
    background-color: #fff;
    opacity: 0.5;
    border-radius: 5px;
  }
  .sao-content_img {
    position: absolute;
    bottom: 0;
    right: 0;
    width: 132px;
    height: 132px;
    border-radius: 50%;
    background-image: url('../assets/hp.jpeg');
    background-size: 100%;
    background-repeat: no-repeat;
    animation: zhuan 10s linear .5s infinite;
  }
}
.snow {
    position: absolute;
    width: 10px;
    height: 10px;
    background-image: url("../assets/dangao.webp");
    background-size: cover;
}
 
@keyframes move1{
    0%{
        top: 0;
        left: var(--left-ini);
        transform: translate(var(--left-ini),-5vh) scale(var(--size));
    }
 
    100%{
        top: 100vh;
        left: var(--left-end);
        transform: translate(var(--left-end),100vh);
    }
}
 
@for $i from 1 through 200 {
    .snow:nth-child(#{$i}) {
        --left-ini: #{random(50)}vw;
        --left-end: #{random(50)}vw;
        --size: #{random(3)};
        // top: -5vh;
        left: #{random(50)}vw;
        animation: move1 #{8 + random(30)}s linear -#{random(20)}s infinite;
    }
}
</style>

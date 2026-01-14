<template>
  <div class="container">
    <div class="ctitle">宫崎骏经典画面</div>
    <!--新的轮播图部分-->
    <div class="banner-container" @mouseenter="stopAutoSlide" @mouseleave="startAutoSlide">
      <div class="banner-slides" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
        <!-- 轮播项1 -->
        <div class="banner-slide">
          <img src="../../assets/images/qian2.jpg" alt="宫崎骏动画场景1" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《千与千寻》经典场景</div>
          </div>
        </div>
        <!-- 轮播项2 -->
        <div class="banner-slide">
          <img src="../../assets/images/totoro2.jpg" alt="宫崎骏动画场景2" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《龙猫》温馨画面</div>
          </div>
        </div>
        <!-- 轮播项3 -->
        <div class="banner-slide">
          <img src="../../assets/images/castle_sky1.jpg" alt="宫崎骏动画场景3" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《天空之城》梦幻场景</div>
          </div>
        </div>
        <!-- 轮播项4 -->
        <div class="banner-slide">
          <img src="../../assets/images/haer2.jpg" alt="宫崎骏动画场景4" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《哈尔的移动城堡》浪漫画面</div>
          </div>
        </div>
        <!-- 轮播项5 -->
        <div class="banner-slide">
          <img src="../../assets/images/boniu3.jpg" alt="宫崎骏动画场景5" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《悬崖上的金鱼姬》相遇场景</div>
          </div>
        </div>
        <!-- 轮播项6 -->
        <div class="banner-slide">
          <img src="../../assets/images/monv1.jpg" alt="宫崎骏动画场景6" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《魔女宅急便》经典场景</div>
          </div>
        </div>
        <!-- 轮播项7 -->
        <div class="banner-slide">
          <img src="../../assets/images/ghost_pricess2.jpg" alt="宫崎骏动画场景7" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《幽灵公主》经典场景</div>
          </div>
        </div>
        <!-- 轮播项8 -->
        <div class="banner-slide">
          <img src="../../assets/images/qifefng3.jpg" alt="宫崎骏动画场景8" class="banner-img">
          <div class="banner-mask">
            <div class="banner-text">《风之谷》经典场景</div>
          </div>
        </div>
      </div>
      
      <!-- 导航按钮 -->
      <div class="banner-nav">
        <button class="banner-btn prev-btn" @click="showPrevSlide">‹</button>
        <button class="banner-btn next-btn" @click="showNextSlide">›</button>
      </div>
      
      <!-- 指示点 -->
      <div class="banner-dots">
        <button class="banner-dot" :class="{ active: currentSlide === 0 }" @click="goToSlide(0)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 1 }" @click="goToSlide(1)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 2 }" @click="goToSlide(2)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 3 }" @click="goToSlide(3)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 4 }" @click="goToSlide(4)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 5 }" @click="goToSlide(5)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 6 }" @click="goToSlide(6)"></button>
        <button class="banner-dot" :class="{ active: currentSlide === 7 }" @click="goToSlide(7)"></button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

// 响应式数据
const currentSlide = ref(0);
const slidesCount = 8; // 轮播图总数
let autoSlideInterval = ref(null);

// 跳转到指定幻灯片
const goToSlide = (slideIndex) => {
  currentSlide.value = slideIndex;
  // 边界处理
  if (currentSlide.value >= slidesCount) currentSlide.value = 0;
  if (currentSlide.value < 0) currentSlide.value = slidesCount - 1;
};

// 上一张
const showPrevSlide = () => goToSlide(currentSlide.value - 1);
// 下一张
const showNextSlide = () => goToSlide(currentSlide.value + 1);

// 开始自动轮播
const startAutoSlide = () => {
  stopAutoSlide(); // 清除旧定时器
  autoSlideInterval.value = setInterval(showNextSlide, 5000); // 5秒切换一次
};

// 停止自动轮播
const stopAutoSlide = () => {
  if (autoSlideInterval.value) clearInterval(autoSlideInterval.value);
};

// 挂载时初始化轮播
onMounted(() => startAutoSlide());
// 卸载时清除定时器（防止内存泄漏）
onUnmounted(() => stopAutoSlide());
</script>

<style scoped>
/* 通用容器样式 */
.container {
  border: 1px solid #e0e9df;
  padding: 40px 30px;
  margin: 40px auto;
  width: 85%;
  background-color: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.05);
  transition: all 0.3s ease;
}

.container:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.1);
}

.ctitle {
  font-size: 24px;
  color: #0d47a1;
  margin-bottom: 25px;
  text-align: center;
  font-weight: 600;
  position: relative;
  padding-bottom: 10px;
}

.ctitle::after {
  content: "";
  display: block;
  width: 80px;
  height: 2px;
  background: #2196f3; 
  margin: 8px auto 0;
  border-radius: 2px;
}

/* ========== 新轮播图样式部分 ========== */
.banner-container {
  position: relative;
  width: 100%;
  height: 420px;
  overflow: hidden;
  border-radius: 8px;
  margin: 0 auto;
}

.banner-slides {
  display: flex;
  transition: transform 0.8s ease;
  height: 100%;
}

.banner-slide {
  min-width: 100%;
  height: 100%;
  position: relative;
}

.banner-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.8s ease;
}

.banner-container:hover .banner-img {
  transform: scale(1.02);
}

.banner-mask {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100px;
  background: linear-gradient(transparent, rgba(0,0,0,0.5));
  display: flex;
  align-items: flex-end;
  padding: 20px;
}

.banner-text {
  color: #fff;
  font-size: 18px;
  text-shadow: 0 1px 3px rgba(0,0,0,0.3);
}

/* 轮播导航按钮 */
.banner-nav {
  position: absolute;
  top: 50%;
  width: 100%;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%);
  padding: 0 15px;
  z-index: 2;
}

.banner-btn {
  background: rgba(255, 255, 255, 0.2);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  color: white;
  font-size: 20px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  backdrop-filter: blur(5px);
}

.banner-btn:hover {
  background: rgba(255, 255, 255, 0.3);
  transform: scale(1.1);
}

/* 轮播指示点 */
.banner-dots {
  position: absolute;
  bottom: 20px;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;
  gap: 10px;
  z-index: 2;
}

.banner-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.banner-dot.active {
  background: white;
  transform: scale(1.2);
}
/* ========== 轮播图样式结束 ========== */

/* 响应式适配 */
@media (max-width: 768px) {
  .container {
    width: 95%;
    padding: 30px 20px;
  }
  .banner-container {
    height: 300px;
  }
  .banner-btn {
    width: 35px;
    height: 35px;
    font-size: 18px;
  }
}

@media (max-width: 480px) {
  .banner-dots {
    bottom: 10px;
  }
}
</style>
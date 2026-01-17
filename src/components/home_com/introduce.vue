<template>
  <!-- 简单介绍 -->
  <div class="container">
    <div class="ctitle">关于宫崎骏</div>
    <p class="text">
      宫崎骏是日本著名动画导演、编剧、漫画家，吉卜力工作室核心人物。其作品以细腻的画风、温暖的故事内核、深刻的人文关怀和环保主题著称，
      代表作包括《千与千寻》《龙猫》《天空之城》《哈尔的移动城堡》等。他的动画里总有蔚蓝的天空、青翠的草地、温柔的风，
      用最纯粹的画面讲述关于成长、勇气、自然与爱的故事，影响了全球无数动画爱好者，也让成年人找回内心的童真。
    </p>
  </div>
</template>

<script setup>
</script>

<style scoped>
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

/* 简介文字样式 */
.text {
  font-size: 17px;
  color: #444;
  line-height: 1.8;
  text-align: center;
  padding: 0 60px;
  text-indent: 2em;
}

.text::first-letter {
  font-size: 24px;
  color: #0d47a1; 
  font-weight: 600;
}

/* 响应式适配 */
@media (max-width: 768px) {
  .container {
    width: 95%;
    padding: 30px 20px;
  }
  .text {
    padding: 0 20px;
  }
}
</style>
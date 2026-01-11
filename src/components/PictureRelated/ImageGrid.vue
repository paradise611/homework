<template>
  <div class="img-container">
    <div 
      v-for="(image, index) in images" 
      :key="index"
      class="img-item"
    >
      <img :src="image.url" :alt="image.alt">
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  // 接收图片数据数组，包含 url 和 alt 属性
  images: {
    type: Array,
    required: true,
    default: () => []
  }
});
</script>

<style scoped>
/* 确保这些变量已在全局 CSS 中定义 */

/* ========== 核心样式：图片网格容器 (.img-container) ========== */
.img-container {
  display: flex;
  flex-wrap: wrap; /* 允许换行 */
  gap: 20px; /* 图片间距 */
  padding: 20px;
  margin-bottom: 3rem;
  justify-content: center; /* 居中对齐 */
}

/* 图片项 (.img-item) */
.img-item {
  /* 默认 4 列布局 ( calc(100% / 4 - 间隙) ) */
  flex: 0 0 calc(25% - 20px); 
  min-width: 200px; /* 最小宽度限制 */
  max-width: 100%;
}

/* 图片元素样式 */
.img-item img {
  width: 100%;
  height: 200px; /* 固定高度 */
  object-fit: cover;
  border-radius: 8px;
  cursor: pointer;
  transition:all 0.3s ease;
}

/* 悬停效果 */
.img-item img:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 12px rgba(0, 0, 0, 0.15);
}

/* ========== 响应式设计 ========== */

/* 平板设备 (1024px 以下) - 切换为 3 列 */
@media (max-width: 1024px) {
  .img-item {
    /* calc(100% / 3 - 间隙) */
    flex: 0 0 calc(33.333% - 20px); 
  }
}

/* 大屏手机 (768px 以下) - 切换为 2 列 */
@media (max-width: 768px) {
  .img-item {
    /* calc(100% / 2 - 间隙) */
    flex: 0 0 calc(50% - 20px); 
    min-width: 150px;
  }
}

/* 小屏手机 (576px 以下) - 切换为 1 列 (并限制最大宽度) */
@media (max-width: 576px) {
  .img-container {
    padding: 10px;
    gap: 15px;
  }
  
  .img-item {
    /* 100% 宽度 */
    flex: 0 0 100%; 
    max-width: 300px; /* 限制单列的最大宽度，避免拉伸过长 */
  }
}
</style>
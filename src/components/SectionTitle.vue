<template>
  <h3 class="section-title">
    {{ title }}
  </h3>
</template>

<script setup>
import { defineProps } from 'vue';

// 定义组件接收的属性 (Props)
const props = defineProps({
  // 标题文本
  title: {
    type: String,
    required: true,
    default: '默认章节标题',
  },
});
</script>

<style scoped>

:root {
  /* 假设这些变量已在全局定义 */
  --secondary-color:#062d5a;
}

.section-title {
  font-size: 1.8rem;
  margin-left: 0.5rem;
  margin-bottom: 1rem;
  color: var(--secondary-color); /* 使用全局定义的颜色变量 */
  position: relative;
  padding-bottom: 0.5rem; /* 留出空间给下方的伪元素下划线 */
}


.section-title::after {
  content: ''; /* 伪元素内容必须设置 */
  position: absolute;
  bottom: 0; /* 定位在 h3 底部 */
  left: 0; /* 从 h3 左侧开始 */
  width: 60px; /* 下划线宽度 */
  height: 4px; /* 下划线高度 */
  background-color: rgb(62, 96, 135); /* 下划线颜色 */
  border-radius: 2px;
}

@media (max-width: 768px) {
  .section-title {
    font-size: 1.5rem;
  }
}
</style>
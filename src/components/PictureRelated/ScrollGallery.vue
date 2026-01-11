<template>
  <div class="picture-container1" ref="scrollContainer">
    <div 
      v-for="(image, index) in renderedImages" 
      :key="index"
      class="picture-item"
    >
      <img :src="image.url" :alt="image.alt">
    </div>
  </div>
</template>

<script setup>
import { defineProps, ref, onMounted, onUnmounted } from 'vue';

const props = defineProps({
  // 接收的图片数组，包含 url 和 alt 属性
  images: {
    type: Array,
    required: true,
    default: () => []
  }
});

// ----------------------------------------------------
// 1. 响应式状态和 DOM 引用
// ----------------------------------------------------

// 用于引用 <div class="picture-container1"> 元素的 DOM 实例
const scrollContainer = ref(null); 
// 存储用于渲染的图片列表 (原始图片 + 复制的图片)
const renderedImages = ref([]); 
// 用于存储自动轮播的定时器
let autoScrollTimer = null; 
// 图片项的宽度 (原 CSS 设为 200px) + gap (原 CSS 设为 10px 左右，这里取 3rem ≈ 48px)
const scrollStep = 248; 


// ----------------------------------------------------
// 2. 无限滚动逻辑实现 (onMounted)
// ----------------------------------------------------

// 滚动逻辑函数
const handleScroll = () => {
  if (!scrollContainer.value) return;

  const container = scrollContainer.value;
  const containerWidth = container.clientWidth;
  const scrollWidth = container.scrollWidth;
  const scrollLeft = container.scrollLeft;

  // 当滚动到接近末尾时 (即复制部分的开始)，瞬间跳回起始位置
  // 假设复制部分是整个列表的一半
  if (scrollLeft >= scrollWidth / 2) {
    // 跳转到原始列表的起始位置
    container.scrollLeft = scrollLeft - scrollWidth / 2;
  } 
  // 当滚动到接近起始位置时 (即在复制部分之前)，瞬间跳到复制部分的末尾
  else if (scrollLeft <= 0) {
     // 跳转到复制列表的起始位置
    container.scrollLeft = scrollLeft + scrollWidth / 2;
  }
};

// 自动轮播启动函数
const startAutoScroll = () => {
  // 清除旧的定时器，避免重复
  clearInterval(autoScrollTimer); 
  
  // 启动新的自动轮播
  autoScrollTimer = setInterval(() => {
    if (scrollContainer.value) {
      scrollContainer.value.scrollLeft += scrollStep;
    }
  }, 2000); // 3秒滚动一次
};

// 鼠标悬停/离开事件，用于控制自动轮播
const handleMouseEnter = () => clearInterval(autoScrollTimer);
const handleMouseLeave = () => startAutoScroll();


// 组件挂载后执行 DOM 操作和事件绑定
onMounted(() => {
  // 1. 初始化图片列表：原始图片复制一份追加，实现无限循环
  renderedImages.value = [...props.images, ...props.images];

  // 2. 添加滚动事件监听器
  const container = scrollContainer.value;
  if (container) {
    container.addEventListener('scroll', handleScroll);
    container.addEventListener('mouseenter', handleMouseEnter);
    container.addEventListener('mouseleave', handleMouseLeave);
    
    // 3. 启动自动轮播
    startAutoScroll();
  }
});

// 组件卸载前清除定时器和事件监听器，避免内存泄漏
onUnmounted(() => {
  clearInterval(autoScrollTimer);

  const container = scrollContainer.value;
  if (container) {
    container.removeEventListener('scroll', handleScroll);
    container.removeEventListener('mouseenter', handleMouseEnter);
    container.removeEventListener('mouseleave', handleMouseLeave);
  }
});
</script>

<style scoped>
/* 确保这些变量已在全局 CSS 中定义 */


/* ========== 横向滚动画廊 (.picture-container1) ========== */
.picture-container1 {
  display: flex;
  gap: 3rem; /* 约 48px */
  margin-bottom: 3rem;
  padding: 10px 0 10px 0;
  flex-wrap: nowrap; 
  width: 100%;
  overflow-x: auto; /* 核心：横向滚动 */
  overflow-y: hidden;
  scroll-behavior: smooth; 
  background-color: #d5def5;
  border-radius: 8px;
  user-select: none;
}

/* 隐藏滚动条 */
.picture-container1::-webkit-scrollbar {
  display: none;
}
.picture-container1 {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

.picture-item {
  flex: 0 0 auto; 
  width: 200px; /* 固定宽度 */
  height: 150px; /* 固定高度 */
  border-radius: 4px;
  /* 核心：图片旋转效果 */
  transform: rotate(10deg); 
  transition: transform 0.2s ease;
  overflow: hidden;
}

/* hover时还原旋转 */
.picture-item:hover {
  transform: rotate(0deg);
}

.picture-item img {
  width: 100%;
  height: 100%;
  object-fit: cover; 
}

/* 响应式调整 (这里主要针对图片容器的 gap/padding) */
@media (max-width: 768px) {
  .picture-container1 {
    padding: 10px;
    gap: 1.5rem; /* 减小间距 */
  }
  .picture-item {
    width: 150px; /* 减小图片尺寸 */
    height: 100px;
  }
}
@media (max-width: 576px) {
  /* 在小屏手机上，您原 HTML 中去掉了横向滚动，切换成了垂直堆叠 */
  /* 如果要遵循，需要修改 flex-direction: column 和 overflow-x: hidden */
  /* 暂时保持横向滚动，但减少旋转角度，避免内容过多溢出 */
  .picture-item {
    transform: rotate(5deg);
  }
}
</style>
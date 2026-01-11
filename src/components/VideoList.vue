<template>
  <div :class="containerClass">
    <VideoCard 
      v-for="video in videos" 
      :key="video.id"
      :video-src="video.src"
      :content="video.content"
      :publish-time="video.time"
      :play-count="video.views"
    />
  </div>
</template>

<script setup>
import { defineProps, computed } from 'vue';
import VideoCard from './VideoCard.vue'; // 引入我们之前创建的 VideoCard 组件


const props = defineProps({
  // 视频数据数组，类型应为 Array
  videos: {
    type: Array,
    required: true,
    default: () => []
  },
  // 布局类型：'featured' (2列) 或 'latest' (3列)
  layout: {
    type: String,
    validator: (value) => ['featured', 'latest'].includes(value),
    default: 'latest'
  }
});

// 这样可以根据父组件传入的 layout 决定使用哪个网格样式
const containerClass = computed(() => {
  if (props.layout === 'featured') {
    return 'video-container-featured'; // 对应原来的 .video-container1 (2列)
  }
  return 'video-container-latest'; // 对应原来的 .video-container (3列)
});
</script>

<style scoped>


/* -------------------------------------- */
/* 2列布局 (对应原 .video-container1) - 用于“精选视频” */
/* -------------------------------------- */
.video-container-featured {
  display: grid;
  grid-template-columns: repeat(2, 1fr); /* 默认 2 列 */
  gap: 1.8rem;
  padding: 1.8rem;
  margin-top: 0rem;
  margin-bottom: 2rem;
}

/* -------------------------------------- */
/* 3列布局 (对应原 .video-container) - 用于“最新资讯” */
/* -------------------------------------- */
.video-container-latest {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 默认 3 列 */
  grid-auto-rows: minmax(200px, auto);
  gap: 1.5rem;
  margin-bottom: 3rem;
  padding: 1.8rem;
  margin-top: 1rem;
}



/* 针对 992px 以下的布局调整 */
@media (max-width: 992px) {
  /* 3列布局 (latest) 在平板上改为 2 列 */
  .video-container-latest {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* 针对 768px 以下的布局调整 */
@media (max-width: 768px) {
  /* 2列布局 (featured) 和 3列布局 (latest) 在手机上都改为 1 列 */
  .video-container-featured,
  .video-container-latest {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    padding: 1rem; /* 可适当减少小屏 padding */
  }
}
</style>
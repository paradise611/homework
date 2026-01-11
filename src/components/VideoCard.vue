<template>
  <div class="grid-item">
    
    <div class="video-wrapper">
      <iframe 
        :src="videoSrc" 
        scrolling="no" 
        border="0" 
        frameborder="no" 
        framespacing="0" 
        allowfullscreen="true"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      ></iframe>
    </div>

    <p class="item-content">{{ content }}</p>

    <div v-if="publishTime || playCount" class="item-footer">
      <span v-if="publishTime">发布时间：{{ publishTime }}</span>
      <span v-if="playCount">播放量：{{ playCount }}</span>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';


const props = defineProps({
  // B站 iframe 嵌入链接 (必需)
  videoSrc: {
    type: String,
    required: true
  },
  // 视频描述内容
  content: {
    type: String,
    default: '暂无描述信息'
  },
  // 发布时间 (可选，用于“精选视频”部分)
  publishTime: {
    type: String,
    default: null
  },
  // 播放量 (可选，用于“精选视频”部分)
  playCount: {
    type: String,
    default: null
  },
});
</script>

<style scoped>


/* 引入在全局或父组件中定义的 CSS 变量 */
:root {

  --border-radius: 12px;
  --box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  --transition: all 0.3s ease;
  --primary-color:rgb(161, 179, 206);
}

.grid-item {
  background: rgb(253, 253, 253);
  border-radius: var(--border-radius);
  box-shadow: var(--box-shadow);
  padding: 1.2rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: var(--transition);
  border-left: 3px solid var(--primary-color);
  overflow: hidden;
}

.grid-item:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 12px rgba(5, 46, 77, 0.15); /* 悬停阴影优化 */
}

.video-wrapper {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* 16:9 宽高比 */
  margin-bottom: 1rem;
  border-radius: 8px;
  overflow: hidden;
}

.video-wrapper iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: none;
}

.item-content {
  flex-grow: 1; /* 确保内容区域能填满剩余空间 */
  margin: 0;
  color: #555;
  font-size: 1rem;
  line-height: 1.7;
}

.item-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 1.2rem;
  border-top: 1px solid #eee;
  font-size: 0.9rem;
  color: #777;
  margin-top: 1rem; /* 增加一点顶部间距，与内容分隔开 */
}
</style>
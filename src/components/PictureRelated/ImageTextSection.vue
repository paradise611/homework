<template>
  <div class="img-text-section">
    <div class="img-text-container">
      
      <div class="img-text-img">
        <img :src="imageUrl" :alt="title">
      </div>
      
      <div class="img-text-content">
        <h3>{{ title }}</h3>
        <p>{{ contentA }}</p>
        <p v-if="contentB">{{ contentB }}</p>
        
        <a :href="buttonUrl" class="img-text-btn">
          {{ buttonText }}
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: { type: String, required: true },
  imageUrl: { type: String, required: true },
  contentA: { type: String, required: true },
  contentB: { type: String, default: null }, // 可选的第二段文字
  buttonText: { type: String, default: '了解更多' },
  buttonUrl: { type: String, default: '#' },
});
</script>

<style scoped>
/* 确保这些变量已在全局 CSS 中定义 */

/* ========== 核心样式：左图右文板块 (.img-text-section) ========== */
.img-text-section {
  
  /* margin: 0 3rem 3rem 3rem; */ 
  margin-bottom: 3rem;
  
  padding: 2rem;
  background: linear-gradient(135deg, #f5f9fc 0%, #e8f4f8 100%);
  border-radius: var(--border-radius);
  box-shadow: var(--box-shadow);
}

.img-text-container {
  display: flex;
  gap: 2.5rem;
  align-items: center;
  flex-wrap: wrap;
}

/* 左侧图片区 */
.img-text-img {
  flex: 0 0 40%;
  min-width: 300px;
}

.img-text-img img {
  width: 100%;
  height: 350px;
  object-fit: cover;
  border-radius: var(--border-radius);
  box-shadow: 0 8px 20px rgba(0,0,0,0.12);
  transition: var(--transition);
}

.img-text-img img:hover {
  transform: scale(1.03);
  box-shadow: 0 6px 12px rgba(69, 80, 90, 0.5);
}

/* 右侧文字区 */
.img-text-content {
  flex: 1;
  min-width: 300px;
}

.img-text-content h3 {
  font-size: 2rem;
  color: var(--primary-color);
  margin-bottom: 1.5rem;
  position: relative;
  padding-bottom: 0.8rem;
}

/* 自定义标题下划线 */
.img-text-content h3::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 80px;
  height: 3px;
  background: var(--accent-color);
  border-radius: 2px;
}

/* 文字内容 */
.img-text-content p {
  color: var(--text-secondary);
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 1.2rem;
}

/* 按钮样式 */
.img-text-btn {
  display: inline-block;
  padding: 0.8rem 2rem;
  background: linear-gradient(to right, var(--primary-color), var(--accent-color));
  color: white;
  text-decoration: none;
  border-radius: 50px;
  font-weight: 500;
  transition: var(--transition);
  box-shadow: 0 4px 12px rgba(74, 144, 226, 0.3);
  margin-top: 1rem;
}

.img-text-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 18px rgba(74, 144, 226, 0.4);
  background: linear-gradient(to right, var(--accent-color), var(--primary-color));
}

/* ========== 响应式设计 ========== */

/* 平板设备 (1024px 以下) */
@media (max-width: 1024px) {
  .img-text-section {
    padding: 1.5rem;
  }
}

/* 手机设备 (768px 以下) - 切换为垂直堆叠 */
@media (max-width: 768px) {
  .img-text-container {
    flex-direction: column;
    gap: 1.5rem;
  }
  
  /* 图片和文字块占据 100% 宽度 */
  .img-text-img, .img-text-content {
    flex: 1;
    min-width: 100%;
  }
  
  .img-text-img img {
    height: 280px;
  }
  
  .img-text-content h3 {
    font-size: 1.7rem;
    /* 手机上标题居中 */
    text-align: center;
  }
  
  /* 标题下划线居中 */
  .img-text-content h3::after {
    left: 50%;
    transform: translateX(-50%);
  }
  
  /* 按钮居中 */
  .img-text-btn {
    display: block;
    text-align: center;
    padding: 0.7rem 1.5rem;
  }
}

/* 小屏手机 (576px 以下) */
@media (max-width: 576px) {
  .img-text-section {
    padding: 1.2rem;
    margin-bottom: 1.5rem;
  }
  
  .img-text-img img {
    height: 220px;
  }
}
</style>
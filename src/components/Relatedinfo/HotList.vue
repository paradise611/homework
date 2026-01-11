<template>
  <aside class="sidebar">
    <h3>热点信息</h3>
    <ul class="hot-list">
      <li v-for="(item, index) in hotItems" :key="index">
        <a :href="item.url || '#'" :title="item.title">{{ item.title }}</a>
      </li>
    </ul>
  </aside>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps({
  hotItems: {
    type: Array,
    required: true,
    default: () => []
  }
});
</script>

<style scoped>
/* 侧边栏样式 (.sidebar) */
.sidebar {
  flex: 0 0 300px; /* 固定宽度，与原始 CSS 保持一致 */
  background-color: beige;
  border-right: 3px solid #e74c3c;
  padding: 10px;
  border-radius: 8px;
}

/* 标题和列表容器 */
aside h3 {
  padding-left: 18px;
}
ul {
  list-style: none;
  list-style-position: inside;
  padding-left: 20px;
}
.hot-list {
  list-style: none;

}

/* 列表项 (.hot-list li) */
.hot-list li {
  margin-bottom: 15px;
  padding-bottom: 10px;
  border-bottom: 2px dashed #1c1a1a;
  list-style-type: disc; 
  padding-left: 0;
}

/* 链接样式 */
.hot-list a {
  color: #1e1d1d;
  text-decoration: none;
  display: block;
  padding: 8px 0;
  transition: all 0.3s;
}

.hot-list a:hover {
  color: #3c83e7;
  transform: translateX(3px);
}

.hot-list a:focus {
  color: rgb(9, 31, 114);
  text-decoration: underline;
  outline: none;
}

/* 响应式调整 */
@media (max-width: 992px) {
  .sidebar {
    border-right: none;
    border-top: 3px solid #e74c3c;
    padding-top: 20px;
    margin-top: 20px;
    flex: auto; /* 允许在小屏下自适应 */
    width: 100%;
  }
}
</style>
<template>
  <div class="author-header" :style="headerStyle">
    <div class="hcontainer">
      <h2>作者</h2>
    </div>
  </div>
</template>

<script setup>
// 1. 修正图片导入路径（assets 拼写正确）
import totoroBg from '../../assets/images/totoro2.jpg'

// 2. 用动态style绑定背景图（避开CSS里v-bind的语法标红）
const headerStyle = {
  background: `linear-gradient(90deg, rgba(1, 21, 39, 0.7) 0%, rgba(171, 198, 229, 0.4) 50%, rgba(0,0,0,0) 100%), url(${totoroBg})`,
  backgroundSize: 'cover',
  color: 'white',
  padding: '6rem 1rem',
  marginBottom: '2rem'
}
</script>
<style scoped>
.hcontainer {
  text-align: left;
  max-width: 600px;
  margin-left: 2rem;
  max-width: 1200px;
  margin: 0 auto 0 2rem; 
}
.author-header h2 {
  font-size: 2.5rem;
  margin: 0;
}
@media (max-width: 768px) {
  .author-header {
    padding: 4rem 1rem !important; 
  }
}
</style>
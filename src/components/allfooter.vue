import allfooter from './components/allfooter.vue';
<template>
  <!-- 页脚 -->
  <footer>
    <div class="ftext">
      <p>宫崎骏动漫网 © 2025 | 治愈每一个热爱动画的你</p>
      <p>所有作品版权归吉卜力工作室及相关权利人所有</p>
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
footer {
  background: linear-gradient(135deg, #0d47a1 0%, #1565c0 100%);
  color: #fff;
  padding: 30px 0;
  text-align: center;
  margin-top: 60px;
  box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
}

.ftext {
  font-size: 14px;
  opacity: 0.9;
  line-height: 1.8;
}

.ftext a {
  color: #bbdefb; 
  text-decoration: none;
}

.ftext a:hover {
  text-decoration: underline;
}
</style>
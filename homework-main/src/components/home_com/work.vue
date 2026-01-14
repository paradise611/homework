<template>
  <div>
    <div class="laber">作品图集</div>
    <div class="container">
      <div class="ctitle">宫崎骏经典作品精选</div>
      <!-- 图片展示区-->
      <div class="icontainer">
        <div class="iitem">
          <img src="../../assets/images/sky.jpg" alt="天空之城" class="img">
          <p class="idesc">天空之城</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/qian3.jpg" alt="千与千寻" class="img">
          <p class="idesc">千与千寻</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/longmao.jpg" alt="龙猫" class="img">
          <p class="idesc">龙猫</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/haer3.jpg" alt="哈尔的移动城堡" class="img">
          <p class="idesc">哈尔的移动城堡</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/monv.jpg" alt="魔女宅急便" class="img">
          <p class="idesc">魔女宅急便</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/ghost_princess1.jpg" alt="幽灵公主" class="img">
          <p class="idesc">幽灵公主</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/qifengle.jpg" alt="风之谷" class="img">
          <p class="idesc">风之谷</p>
        </div>
        <div class="iitem">
          <img src="../../assets/images/fish.jpg" alt="悬崖上的金鱼姬" class="img">
          <p class="idesc">悬崖上的金鱼姬</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
/* 标签样式 */
.laber {
  font-size: 20px;
  color: #0d47a1; 
  margin: 0 0 15px 7.5%;
  font-weight: 600;
  display: flex;
  align-items: center;
}

.laber::before {
  margin-right: 10px;
  font-size: 22px;
}

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

/* 图片展示区 */
.icontainer {
  display: flex;
  flex-wrap: wrap;
  gap: 25px;
  justify-content: center;
}

.iitem {
  width: calc(25% - 19px); 
  border-radius: 8px;
  overflow: hidden;
  background: #f9f9f9;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  transition: all 0.4s ease;
}

.iitem:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 8px 15px rgba(0,0,0,0.15);
}

.img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  transition: all 0.3s ease;
}

.iitem:hover .img {
  filter: brightness(1.05);
}

.idesc {
  text-align: center;
  padding: 12px 0;
  color: #333;
  font-size: 15px;
  font-weight: 500;
}

/* 响应式适配 */
@media (max-width: 1200px) {
  .iitem {
    width: calc(33.33% - 17px);
  }
}

@media (max-width: 768px) {
  .container {
    width: 95%;
    padding: 30px 20px;
  }
  .iitem {
    width: calc(50% - 12px);
  }
}

@media (max-width: 480px) {
  .iitem {
    width: 100%; 
  }
}
</style>
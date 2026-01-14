<template>
  <div>
    <div class="laber">二创作品</div>
    <div class="container">
      <div class="ctitle">治愈系二创视频合集</div>
      <div class="vlist">
        <div class="vitem">
          <iframe src="https://player.bilibili.com/player.html?isOutside=true&aid=824221298&bvid=BV1tg4y13712&cid=1073811297&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
        </div>
        <div class="vitem">
          <iframe src="https://player.bilibili.com/player.html?isOutside=true&aid=1856610553&bvid=BV1PW421X7bQ&cid=1659148273&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
        </div>
        <div class="vitem">
          <iframe src="https://player.bilibili.com/player.html?isOutside=true&aid=754091002&bvid=BV1yk4y1m792&cid=218653972&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
        </div>
        <div class="vitem">
          <iframe src="https://player.bilibili.com/player.html?isOutside=true&aid=91811122&bvid=BV1A7411K7bB&cid=156708142&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
        </div>
        <div class="vitem">
         <iframe src="https://player.bilibili.com/player.html?isOutside=true&aid=784128913&bvid=BV1424y1A77Y&cid=1147210744&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
        </div>
        <div class="vitem">
         <iframe src="https://player.bilibili.com/player.html?isOutside=true&aid=455777176&bvid=BV1o5411s7Af&cid=334018435&p=1&autoplay=0" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>
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

.vlist {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 25px;
  width: 100%;
  margin: 0 auto;
}

.vitem {
  background: #fff;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  transition: all 0.3s ease;
  border: 1px solid #e0e9df;
}

.vitem:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.12);
}

/* 视频iframe样式 */
.vitem iframe {
  width: 100%;
  height: 300px;
  border: none;
  border-radius: 0;
}

/* 响应式调整 */
@media (max-width: 1200px) {
  .vlist {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .container {
    width: 95%;
    padding: 30px 20px;
  }
  .vlist {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .vitem iframe {
    height: 280px;
  }
}

@media (max-width: 480px) {
  .vitem iframe {
    height: 200px;
  }
}
</style>
<template>
    <Nav />
  <Sakura />
  <Header 
    title="相关资讯" 
    :background-image-url="headerImage"
  />
    
    <main class="container">
      
      <SectionTitle title="最新资讯" />

      <InfoPageLayout>
        <template #main-content>
          <InfoCard
            v-for="(item, index) in latestArticles"
            :key="index"
            :image-url="item.imageUrl"
            :title="item.title"
            :description="item.description"
            :url="item.url"
          />
        </template>
        
        <template #sidebar>
          <HotListSidebar :hot-items="hotItems" />
        </template>
      </InfoPageLayout>
      
      <SectionTitle title="精选视频" />
      
      <div class="container2">
        <InfoCard
          v-for="(item, index) in videoItems"
          :key="index"
          :image-url="item.imageUrl"
          :title="item.title"
          :description="item.description"
          :url="item.url"
        />
      </div>
      
    </main>
    
    <AppFooter />
  
</template>

<script setup>
import Nav from '../components/Nav.vue';
import Sakura from '../components/Sakura.vue'; 
import Header from '../components/Header.vue';
import { ref } from 'vue';

import qian1Image from '../assets/images/qian1.jpg'; 
const headerImage = ref(qian1Image);
import SectionTitle from '../components/SectionTitle.vue';

import InfoPageLayout from '../components/Relatedinfo/Layout.vue';
import HotListSidebar from '../components/Relatedinfo/HotList.vue';
import InfoCard from '../components/Relatedinfo/infoCard.vue';

// --- 数据定义 ---

// 1. 最新资讯数据 (对应 .main-container1 中的两个 .grid-item)
const latestArticles = ref([
  { imageUrl: 'src/assets/images/castle_sky2.jpg', title: '天空之城创作背景解析', description: '简要介绍天空之城的创作灵感、时代背景等。', url: 'https://zhuanlan.zhihu.com/p/633489395' },
  { imageUrl: 'src/assets/images/haer2.jpg', title: '哈尔的移动城堡创作背景解析', description: '简要介绍哈尔的移动城堡的创作灵感、时代背景等。', url: 'https://example.com/sky-castle' },
]);

// 2. 热点信息数据 (对应 .hot-list)
const hotItems = ref([
  { title: '宫崎骏新作最新消息', url: '#' },
  { title: '吉卜力美术馆参观指南', url: '#' },
  { title: '经典动画重映时间表', url: '#' },
  { title: '动画配乐背后的故事', url: '#' },
  { title: '角色设计灵感来源', url: '#' },
]);

// 3. 精选视频数据 (对应 .container2 中的八个 .grid-item)
const videoItems = ref([
  { imageUrl: 'src/assets/images/castle_sky1.jpg', title: '天空之城经典镜头混剪', description: '时长5分钟，包含多个经典画面和配乐。', url: 'https://example.com/sky-video1' },
  { imageUrl: 'src/assets/images/totoro1.jpg', title: '龙猫制作幕后花絮', description: '揭秘龙猫角色设计和场景搭建的过程。', url: 'https://example.com/totoro-video' },
  { imageUrl: 'src/assets/images/qian1.jpg', title: '千与千寻深层含义解析', description: '从文化、哲学角度解读千与千寻的隐藏剧情。', url: 'https://example.com/spirited-video' },
  { imageUrl: 'src/assets/images/qian1.jpg', title: '千与千寻深层含义解析', description: '从文化、哲学角度解读千与千寻的隐藏剧情。', url: 'https://example.com/spirited-video' },
  { imageUrl: 'src/assets/images/monv.jpg', title: '千与千寻深层含义解析', description: '从文化、哲学角度解读千与千寻的隐藏剧情。', url: 'https://example.com/spirited-video' },
  { imageUrl: 'src/assets/images/castle_sky2.jpg', title: '《天空之城》的背景故事', description: '摘自豆瓣，这篇影评可能有剧透。', url: 'https://movie.douban.com/review/9685152/' },
  { imageUrl: 'src/assets/images/qian1.jpg', title: '千与千寻深层含义解析', description: '从文化、哲学角度解读千与千寻的隐藏剧情。', url: 'https://example.com/spirited-video' },
  { imageUrl: 'src/assets/images/haer1.jpg', title: '千与千寻深层含义解析', description: '从文化、哲学角度解读千与千寻的隐藏剧情。', url: 'https://example.com/spirited-video' },
]);
</script>

<style scoped>
/* 仅保留页面特定的布局样式和容器样式 */
.container {
  background-color: aliceblue;
  padding: 1rem;
  margin: 3rem auto;
  max-width: 1200px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.05);
}

.divider-horizontal {
  border: none;
  height: 3px;
  background: linear-gradient(to right, #007bff, #28a745, #ffc107);
  margin: 0 auto 3rem;
  max-width: 1200px;
}

/* container2 视频网格样式 */
.container2 {
  display: grid; 
  background-color: #f9f9f9;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); 
  gap: 25px; 
  padding: 10px 0;
}

</style>
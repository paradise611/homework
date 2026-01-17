<template>
  <div class="icontainer">
    <div class="parea">
      <div class="pcontainer">
        <img :src="authorImg" alt="宫崎骏照片" class="photo">
      </div>
    </div>
    <div class="carea">
      <h1>宫崎骏</h1>
      <div class="text">
        <p>宫崎骏，1941年1月5日出生于日本东京都文京区，1963年毕业于日本东京学习院大学政治经济部。日本动画师、动画制作人、漫画家、动画导演、动画编剧。</p>
        <p>1963年，宫崎骏进入东映动画公司，从事动画师工作。1971年，和高畑勋一起加入A Production，并合作导演《鲁邦三世》第一季。1979年，转入东京电影新社创作首部电影《鲁邦三世：卡里奥斯特罗之城》。1982年，开始独立创作漫画，在《Animage》上连载漫画《风之谷》，并获得第23届日本漫画家协会赏。</p>
        <p>1985年，与高畑勋、铃木敏夫共同创立吉卜力工作室。1986年，执导《天空之城》，该片获得第41回每日电影奖大藤信郎赏等6项大奖。1988年，执导《龙猫》，该片荣获第13回报知电影奖最佳导演奖等24项大奖。</p>
        <p>2001年，执导《千与千寻》，该片荣获第75届奥斯卡金像奖最佳动画长片奖、第52届柏林国际电影节金熊奖等9项大奖。2004年，执导《哈尔的移动城堡》，该片荣获第9届好莱坞电影奖最佳动画片奖等8项大奖。</p>
        <p>2023年7月14日，《你想活出怎样的人生》在日本上映，并获得第96届奥斯卡金像奖最佳动画长片奖等一众奖项。2024年1月5日，阿里影业与吉卜力工作室达成合作。</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import authorImg from '../../assets/images/author2.jpg'
</script>
<style scoped>
.pcontainer .photo {
  max-width: 100%;
  height: auto;
  display: block;
}
</style>
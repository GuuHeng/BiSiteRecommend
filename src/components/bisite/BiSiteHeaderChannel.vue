
<template>
  <div class="header_channels">
    <ul class="header_channels_leftArea">
      <li v-for="(item, index) in leftAreaChannelsData" :key="index">
        <a>
          <img src="@/images/header_left_01.jpeg" alt="{{ item.name }}" width="50" height="50" />
          <span>{{ item.name }}</span>
        </a>
      </li>
    </ul>
    <div class="header_channels_centerArea">
      <a v-for="(item, index) in centerAreaChannelsData" :key="index" class="header_channels_centerArea_item"
        @mouseover="handleMouseOver($event, item)">
        {{ item.name }}
      </a>
      <!-- <BiSiteHeaderSubChannelsExtensionView @mouseover="handleMouseOver"></BiSiteHeaderSubChannelsExtensionView> -->
    </div>
    <div class="header_channels_rightArea">
      <a v-for="(item, index) in rightAreaChannelsData" :key="index" target="_blank" href="{{ item.url }}">
        <!-- <img src="{{ item.icon }}"> -->
        <IconZhuanlan></IconZhuanlan>
        <span>{{ item.name }}</span>
      </a>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
// eslint-disable-next-line no-unused-vars
// import BiSiteHeaderSubChannelsExtensionView from './components/bisite/BiSiteHeaderSubChannelsExtensionView.vue'
import IconZhuanlan from '../icons/IconZhuanlan.vue'

const leftAreaChannelsData = [
  { icon: '@/images/header_left_01.jpeg', name: '动态' },
  { icon: '@/images/header_left_01.jpeg', name: '热门' },
  { icon: 'https://i2.hdslb.com/bfs/face/1ec6cf668a98930bad7a3da1c748ad934aed9860.jpg@92w_92h', name: '频道' },
]

const centerAreaChannelsData = [
  {
    name: '番剧',
    url: '//www.bilibili.com/anime/',
    subChannels:
      [{ name: "连载漫画", url: '//www.bilibili.com/anime/' },
      { name: "新番时间表", url: '//www.bilibili.com/anime/' },
      { name: "完结动画", url: '//www.bilibili.com/anime/' },
      { name: "番剧索引", url: '//www.bilibili.com/anime/' },
      { name: "资讯", url: '//www.bilibili.com/anime/' },
      { name: "官方延伸", url: '//www.bilibili.com/anime/' }]
  },
  { name: '电影', url: '#' },
  { name: '国创', url: '//www.bilibili.com/guochuang/' },
  { name: '电视剧', url: '#' },
  { name: '综艺', url: '#' },
  { name: '纪录片', url: '#' },
  { name: '动画', url: '#' },
  { name: '游戏', url: '#' },
  { name: '鬼畜', url: '#' },
  { name: '音乐', url: '#' },
  { name: '舞蹈', url: '#' },
  { name: '影视', url: '#' },
  { name: '娱乐', url: '#' },
  { name: '知识', url: '#' },
  { name: '科技', url: '#' },
  { name: '资讯', url: '#' },
  { name: '美食', url: '#' },
  { name: '生活', url: '#' },
  { name: '汽车', url: '#' },
  { name: '时尚', url: '#' },
  { name: '运动', url: '#' },
  { name: '动物圈', url: '#' },
  { name: 'VLOG', url: '#' },
  { name: '更多', url: '#' }]

const rightAreaChannelsData = [
  { name: '专栏', url: '#', icon: '@/images/header_left_01.jpeg' },
  { name: '直播', url: '#', icon: '@/images/header_left_01.jpeg' },
  { name: '活动', url: '#', icon: '@/images/header_left_01.jpeg' },
  { name: '课堂', url: '#', icon: '@/images/header_left_01.jpeg' },
  { name: '社区中心', url: '#', icon: '@/images/header_left_01.jpeg' },
  { name: '新歌热榜', url: '#', icon: '@/images/header_left_01.jpeg' },
]


const isHover = ref(false);
isHover.value = true;

// eslint-disable-next-line no-unused-vars
function handleMouseOver(event, item) {
  if (item.subChannels.length > 0) {
    let array = item.subChannels
    var text = array.first.name
    for (let index = 0; index < array.length; index++) {
      // const element = array[index];
      alert(text)
    }
  }
}

</script>

<style scoped>
/* 2*/
.header_channels {
  height: 110px;
  margin: 0 auto;
  padding: 0;
  display: flex;
  align-items: center;
  background-color: white;
  justify-content: space-between;
}

@media (min-width: 1550px) {
  .header_channels {
    padding: 0 140px;
  }
}

.header_channels_leftArea {
  width: 210px;
  display: flex;
  justify-content: space-between;
  flex-shrink: 0;
  align-items: center;
  color: black;
  padding: 0;
}

.header_channels_leftArea li:hover {}

.header_channels_leftArea li a {
  height: 70px;
  width: 50px;
  font-size: 14px;
  display: flex;
  flex-direction: column;
  text-align: center;
}

.header_channels_leftArea li a img {
  border-radius: 50%;
  width: 50px;
  height: 50px;
}

.header_channels_centerArea {
  /* min-width: 1200px;
  max-width: 1440px; */
  width: 100%;
  height: 70px;
  display: grid;
  grid-auto-flow: column;
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(12, 1fr);
  grid-gap: 10px;
  margin-left: 20px;
  letter-spacing: 2px;
  /* overflow: hidden; */
  /* background-color: aqua; */
  padding-right: 20px;

  border-right: gray 1px solid;
}

.header_channels_centerArea_item {
  color: rgb(51, 51, 51);
  font-size: 14px;
  background-color: rgb(246, 247, 248);
  text-align: center;
  line-height: 30px;
  height: 30px;
  border-radius: 4px;
}

.header_channels_centerArea_item:hover {
  background-color: rgb(200, 200, 200);
}


.header_channels_rightArea {
  /* background-color: blue; */
  width: 258px;
  display: grid;
  grid-auto-flow: column;
  /* grid-template-columns: repeat(3, 1fr); */
  grid-template-rows: repeat(2, 1fr);
  row-gap: 10px;
  flex-shrink: 0;
  font-size: 14px;
  color: black;
  letter-spacing: 2px;
}

.header_channels_rightArea a {
  color: black;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  height: 32px;
}

.header_channels_rightArea a:hover {
  color: blue;
  fill: blue;
}

BiSiteHeaderSubChannelsExtensionView {
  float: center;
}
</style>
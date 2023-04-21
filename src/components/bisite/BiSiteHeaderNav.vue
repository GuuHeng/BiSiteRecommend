<template>
  <div class="header">
    <div class="header_navigationbar">
      <ul class="channels">
        <li v-for="channel in channelsData" :key="channel.indexOf">
          <RouterLink to="#">{{ channel }}</RouterLink>
        </li>
      </ul>

      <form class="searchBar">
        <input class="search" type="text" name="search" placeholder="鬼灭之刃" />
        <button class="mirror">搜索</button>
      </form>

      <span class="login-entry">登录</span>

      <ul class="user-entrys">
        <li v-for="(item, index) in userEntrysData" :key="index">
          {{ item.name }}
        </li>
      </ul>
    </div>
    <div class="banner">
      <img src="@/images/header_bg.png" alt="导航背景图">
    </div>
  </div>
</template>

<script setup>
import { RouterLink } from 'vue-router';

const channelsData = [
  '首页',
  '番剧',
  '直播',
  '游戏中心',
  '会员购',
  '漫画',
  '赛事',
  '春日',
  '下载客户端'
]

const userEntrysData = [
  { icon: '', name: '大会员' },
  { icon: '', name: '消息' },
  { icon: '', name: '动态' },
  { icon: '', name: '收藏' },
  { icon: '', name: '历史' },
  { icon: '', name: '创作中心' }
]


</script>

<style scoped>
.header {
  width: 100%;
  min-height: 155px;
  max-height: 245px;
  background-color: orchid;
  display: block;
  height: 9vw
}

.banner {
  height: 100%;
  background-color: blue;
  display: block;
}

.banner img {
  height: 100%;
  width: 100%;
  object-fit: cover;
  margin: 0;
  top: 0;
  display: block;
}

.header_navigationbar {
  position: absolute;
  width: 100%;
  height: 64px;
  display: flex;
  align-items: center;
  margin: 0px;
  justify-content: space-between;
  z-index: 1;
}

.header_navigationbar .channels {
  display: flex;
  flex-shrink: 0;
}

.header_navigationbar .channels li {
  padding: 0 10px;
}

.header_navigationbar .channels li a {
  color: white;
  font-size: 15px;
  line-height: 40px;
  max-lines: 1;
}

.searchBar {
  background-color: white;
  opacity: 0.85;
  height: 40px;
  border-radius: 8px;
  border-width: 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  flex: 1 auto;
  flex-shrink: 0;
}

.searchBar:hover {
  opacity: 1;
}

.search {
  font-size: 15px;
  padding: 0 5px;
  border-width: 0;
  min-width: 200px;
}

.search:focus {
  background-color: lightblue;
  border-width: 0;
}

.mirror {
  /* width: 50px; */
  background-color: white;
  width: 60px;
  vertical-align: middle;
  border-width: 0;
}

.login-entry {
  width: 40px;
  height: 40px;
  background-color: dodgerblue;
  border-radius: 50%;
  color: white;
  font-size: 14px;
  text-align: center;
  line-height: 40px;
  margin-left: 10px;
  flex-shrink: 0;
}

.user-entrys {
  display: flex;
  flex-shrink: 0;
}

.user-entrys li {
  padding: 0 10px;
  color: white;
}
</style>



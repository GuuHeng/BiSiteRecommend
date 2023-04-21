<template>
    <div class="feed">
        <div class="recommend_banner">
            <swiper class="recommend_banner_swiper" :modules=swiper_modules :pagination="{ clickable: true }"
                :autoplay="{ delay: 3000, disableOnInteraction: false }" :loop="true" :spaceBetween="50"
                :navigation="navigation" :slidesPerView="1">
                <SwiperSlide :zoom="true" class="recommend_banner_swiper_slide" v-for="(item, index) in feed_banners"
                    :key="index">
                    <img class="recommend_banner_swiper_slide_img" :src="item.img" alt="" referrerpolicy="no-referrer">
                </SwiperSlide>

                <div class="swiper-pagination"></div>
                <div class="swiper-button-prev"></div>
                <div class="swiper-button-next"></div>
                <div class="swiper-scrollbar"></div>
            </swiper>
            <!-- <swiper class="recommend_banner_swiper" :="banner_swiper">
                <SwiperSlide :zoom="true" class="recommend_banner_swiper_slide" v-for="( item, index ) in  feed_banners "
                    :key="index">
                    <img class="recommend_banner_swiper_slide_img" :src="item.img" alt="" referrerpolicy="no-referrer">
                </SwiperSlide>
                <div class="recommend_banner_pagination">

                </div>
            </swiper> -->
            <div class="recommend_banner_footer">
                <div class="recommend_banner_title">
                </div>
                <div class="recommend_banner_pagination">

                </div>
                <div class="recommend_banner_switch">

                </div>
            </div>
        </div>
        <div class="recommend_card" v-for="( item, index ) in  feed_recommend_cards " :key="index">
            <div class="card_img">
                <a href="https://www.baidu.com">
                    <img :src="item.img" alt="" class="card_video_bgimg" referrerpolicy="no-referrer">
                    <div class="card_video_info">
                        <div class="card_video_info_left">
                            <div class="card_video_views">
                                <IconZhuanlan></IconZhuanlan>
                                {{ item.views }}
                            </div>
                            <div class="card_video_comments">
                                <IconZhuanlan></IconZhuanlan>
                                {{ item.comments }}
                            </div>
                        </div>
                        <span class="card_video_duration">{{ item.duration }}</span>
                    </div>
                </a>
            </div>
            <div class="card_summary">
                <h3 class="title">{{ item.title }}</h3>
                <div>
                    <span class="card_badge" v-if="item.isFocus == true">已关注</span>
                    <span class="card_up_host">{{ item.up_name + "·" + item.up_time }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import IconZhuanlan from '../icons/IconZhuanlan.vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Pagination, Navigation, Scrollbar } from 'swiper'
import 'swiper/css';


const swiper_modules = [Autoplay, Pagination, Navigation, Scrollbar]

//TypeError: Class constructor Swiper cannot be invoked without 'new'
// eslint-disable-next-line no-unused-vars
// const banner_swiper = new Swiper('.swiper', {
//     // Install modules
//     modules: [Autoplay, Pagination, Navigation, Scrollbar],
//     speed: 500,
//     loop: true,
//     pagination: {
//         clickable: true
//     },
//     navigation: {
//         nextEl: '.swiper-button-next',
//         prevEl: '.swiper-button-prev',
//     },
//     autoplay: {
//         delay: 3000
//     },
//     disableOnInteraction: false,
//     spaceBetween: 50,
//     slidesPerView: 1

// });

// 推荐banner
const feed_banners = [
    {
        img: "https://i0.hdslb.com/bfs/banner/d25cdb5841fa2d4b6f5f8d1bd0411a4708ec04ab.png@976w_550h_1c_!web-home-carousel-cover.avif",
        url: ""
    },
    {
        img: "https://i0.hdslb.com/bfs/banner/546451271abf3a2fa665260113f004fd4d708104.png@976w_550h_1c_!web-home-carousel-cover.avif",
        url: ""
    }
]

// function prevEl() {

// }

// function clickBanner(item, index) {

// }


// 推荐内容卡片
const feed_recommend_cards = []
for (let index = 0; index < 100; index++) {
    const element = {
        img: "https://i0.hdslb.com/bfs/archive/0445df7a87ab43716ebc3e285a0fb13f4fac9e18.jpg@672w_378h_1c_!web-home-common-cover",
        views: 100,
        comments: 100,
        duration: "1:30",
        title: "花千万买豪车不让进展台！劳斯莱斯车主被销售看不起...",
        up_name: "酱紫",
        up_time: "2023-04-01",
        likeCount: "2万",
        isFocus: true
    }

    if (index % 2 == 0) {
        element.isFocus = false
    }
    feed_recommend_cards.push(element)
}

</script>


<style scoped>
.feed {
    /* background-color: aqua; */
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-template-rows: 265px;
    gap: 20px;
    padding: 10px 140px;
    flex-shrink: 0;
    color: black;
}


/* #region 推荐banner */
.recommend_banner {
    grid-column: 1 / 3;
    grid-row: 1 / 3;
    background-color: red;
    border-radius: 6px;
    height: 475px;
    overflow: hidden;
    object-fit: cover;
}

.recommend_banner_swiper {
    width: 100%;
    /* height: 100%; */
    object-fit: cover;
    vertical-align: middle;
    height: 180;
}

.recommend_banner_swiper_slide {
    width: 100%;
    height: 100%;
    /* text-align: ; */
}

.recommend_banner_swiper_slide_img {
    width: 100%;
    height: 100%;
    background-color: aqua;
    display: block;
}

.recommend_banner_footer {
    background-color: whitesmoke;
    height: 100%;
}

/* #endregion */

.recommend_card {
    background-color: white;
    height: 265px;
    border-radius: 6px;
    overflow: hidden;
}

.recommend_card img {
    width: 100%;
    height: 190px;
    object-fit: cover;
}

.card_img {
    height: 190px;
}

.card_img a {
    position: relative;
}

/* .card_video_bgimg {
    position: absolute;
} */

/* #region播放量，评论数，时长 */
.card_video_info {
    position: absolute;
    z-index: 2;
    height: 30px;
    left: 0;
    right: 0;
    bottom: 3px;
    display: flex;
    justify-content: space-between;
    padding-left: 5px;
    padding-right: 5px;
    font-size: 13px;
    align-items: end;
    background-image: linear-gradient(180deg, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, .8) 100%);
}

.card_video_info_left {
    display: flex;
    color: white;
    fill: white;
}

.card_video_views {
    display: flex;
    align-items: center;
}

.card_video_comments {
    display: flex;
    align-items: center;
    margin-left: 10px;
}

.card_video_duration {
    display: flex;
    align-items: center;
    color: white;
}

/* #endregion 播放量，评论数，时长 */

.card_summary {
    padding: 0 5px;
    padding-right: 24px;
    font-size: 13px;
    margin-top: 10px;
}

.card_summary .title {
    font-size: 15px;
    font-weight: bold;
    height: 44px;
    line-height: 22px;
}

.card_summary .title:hover {
    color: aqua;
}

.card_badge {
    background-color: #FFF0E3;
    color: orange;
    font-size: 10px;
    padding: 0 2px;
    border-radius: 4px;
}

.card_up_host {
    margin-left: 5px;
    color: gray;
}

.card_up_host:hover {
    color: aqua;
}
</style>
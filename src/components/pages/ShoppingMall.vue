<template>
  <div>
    <!-- 搜索 -->
    <div class="search-bar">
      <van-row>
        <van-col span="3">
          <img :src="location" width="47%" class="search-icon" />
        </van-col>
        <van-col span="15">
          <input type="text" class="search-input" placeholder="查找">
        </van-col>
        <van-col span="6">
          <van-button size="mini" class="search-button">查找</van-button>
        </van-col>
      </van-row>
    </div>
    <!-- swipe 轮播图 -->
    <div class="swipe-area">
      <van-swipe :autoplay="3000" indicator-color="#fff">
        <van-swipe-item v-for="(image, index) in bannerImages" :key="index">
          <img v-lazy="image.image" width="100%"/>
        </van-swipe-item>
      </van-swipe>
    </div>
    <!-- 品类 -->
    <div class="type-bar j-typebar">
      <div v-for="(cate, index) in category" :key="index">
        <img v-lazy="cate.image" />
        <span>{{cate.mallCategoryName}}</span>
      </div>
    </div>
    <!-- 广告 -->
    <div>
      <img v-lazy="advertesPicture" width="100%">
    </div>
    <!-- 推荐商品 -->
    <div class="recommend-area">
      <div class="recommend-title">商品推荐</div>
      <div class="recommend-body">
        <swiper ref="mySwiper" :options="swiperOptions">
          <swiper-slide  v-for="(item, index) in recommendItems" :key="index">
            <div class="recomment-item">
              <img :src="item.image" width="80%">
              <p>{{item.goodsName}}</p>
              <p>￥{{item.price}}(￥{{item.mallPrice}})</p>
            </div>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper';
  import 'swiper/swiper-bundle.css'

  export default {
    data() {
      return {
        msg: 'ShoppingMall',
        location: require('../../assets/location.png'),
        bannerImages: [],
        category: [],
        advertesPicture: '',
        recommendItems: [],
        swiperOptions: {
          slidesPerView: 3
        }
      }
    },
    components: {
      Swiper,
      SwiperSlide
    },
    directives: {
      swiper: directive
    },
    created() {
      axios({
        url: 'https://www.fastmock.site/mock/8b1fee580436e595d0ae54ff0bb3536a/Vue2Koa2/index',
        method: 'get'
      }).then(response => {
        console.log(response);
        if (response.status == 200) {
          this.category = response.data.data.category;
          this.advertesPicture = response.data.data.advertesPicture.PICTURE_ADDRESS;
          this.bannerImages = response.data.data.slides;
          this.recommendItems = response.data.data.recommend
        }
      }).catch(error => {
        console.log(error);
      })
    }
  }
</script>

<style scoped>
  .search-bar {
    height: 2.2rem;
    padding-bottom: 3px;
    line-height: 2.2rem;
    overflow: hidden;
    background: #e5017d;
  }
  .search-icon {
    padding-top: .8rem;
    padding-left: .6rem;
  }
  .search-input {
    width: 100%;
    height: 1.4rem;
    font-size: .7rem;
    padding-left: .2rem;
    color: #fff;
    border-left: 0;
    border-top: 0;
    border-right: 0;
    border-bottom: 1px solid #fff;
    background: #e5017d;
  }
  input::-webkit-input-placeholder {
    /* WebKit browsers */
    color: #999;
    opacity: 1;
  }
  input:-moz-placeholder {
    /* Mozilla Firefox 4 to 18 */
    color: #999;
    opacity: 1;
  }
  input::-moz-placeholder {
    /* Mozilla Firefox 19+ */
    color: #999;
    opacity: 1;
  }
  input:-ms-input-placeholder {
    /* Internet Explorer 10+ */
    color: #999;
    opacity: 1;
  }
  .search-button {
    width: 70%;
    margin-left: .8rem;
    color: #000;
    border-color: #999;
    border-radius: 5px;
    background: #999;
  }
  .swipe-area {
    max-height: 9.15rem;
    clear: both;
    overflow: hidden;
  }
  .type-bar {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    margin: 0 .3rem .3rem .3rem;
    border-radius: .3rem;
    font-size: .8rem;
    background: #fff;
  }
  .type-bar div {
    padding: .3rem;
    text-align: center;
  }
  .type-bar div img {
    width: 3rem;
  }
  .recommend-area {
    margin-top: .3rem;
    background: #fff;
  }
  .recommend-title {
    padding: .2rem;
    border-bottom: 1px solid #eee;
    color: #e5017d;
    font-size: 14px;
  }
  .recommend-body {
    border-bottom: 1px solid #eee;
  }
  .recomment-item {
    width: 99%;
    text-align: center;
    font-size: 12px;
    border-right: 1px solid #eee;
  }
</style>

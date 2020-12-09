<template>
  <div>
    <!-- 搜索 -->
    <div class="search-bar">
      <van-row>
        <van-col span="3">
          <img :src="location" width="45%" class="search-icon" />
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
          <img v-lazy="image.imageUrl" width="100%"/>
        </van-swipe-item>
      </van-swipe>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        msg: 'ShoppingMall',
        location: require('../../assets/location.png'),
        bannerImages: [
          {imageUrl:'http://images.baixingliangfan.cn/advertesPicture/20180407/20180407175040_1780.jpg'},
          {imageUrl:'http://images.baixingliangfan.cn/advertesPicture/20180407/20180407175111_9509.jpg'},
          {imageUrl:'http://images.baixingliangfan.cn/advertesPicture/20180407/20180407175142_6947.jpg'}
        ]
      }
    },
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
    padding-top: .6rem;
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
    max-height: 15rem;
    overflow: hidden;
  }
</style>

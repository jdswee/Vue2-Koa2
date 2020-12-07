<template>
  <div>
    <van-row gutter="20">
      <van-col span="8">span: 8</van-col>
      <van-col span="8">span: 8</van-col>
      <van-col span="8">span: 8</van-col>
    </van-row>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        msg: 'ShoppingMall'
      }
    },
  }
</script>

<style scoped>
  .van-col {
    margin-bottom: 1rem;
    text-align: center;
    background: #39a9ed;
    background-clip: content-box;
  }
</style>

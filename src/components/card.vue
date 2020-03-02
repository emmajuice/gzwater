<template>
  <div class="card-container">
      <div class="card-box" v-for="(list,index) in cardInfo" :key="index">
        <img class="cardImg" :src="list.imageUrl" alt="">
        <span class="product-name">{{list.name}}</span>
        <p class="product-desc">
          {{list.desc}}
        </p>
        <div class="else-options">
          <div class="price">
            <p>￥</p>
            <span>{{list.price}}</span>
          </div>
          <img src="https://www.easyicon.net/api/resizeApi.php?id=1102016&size=128" alt="">
        </div>
      </div>
    </div>
</template>

<script>
export default {
  props: [
    'text',
    'cardInfo'
  ]
}

</script>

<style>
.card-container{
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.card-box{
  background: #fff;
  border-radius: 20rpx;
  padding: 30rpx 20rpx;
  width: 305rpx;
  display: inline-block;
  margin-bottom: 20rpx;
  box-shadow: 0 0 12rpx 2rpx #eee;
}
.cardImg{
  width: 100%;
  height: 240rpx;
  max-height: 240rpx;
}
.product-name{
  color: #333;
  font-size: 26rpx;
  font-weight: 600;
}
.product-desc{
  font-size: 22rpx;
}
.else-options{
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 8rpx
}
.price{
  color:red;
}
.price p{
  font-size: 26rpx;
  display: inline-block;
  vertical-align: center;
}
.price span{
  font-size: 34rpx;
}
.else-options img{
  width: 36rpx;
  height: 36rpx;
}
</style>

<template>
  <div class="shop-container">
    <div class="shop-header">
        <div class="shopImg">
          <img src="https://www.mywhh.com/pc/img/test-title.png" alt="">
        </div>
        <div class="shopIofo">
            <h2>中坝水站（676004）</h2>
            <van-rate
              readonly
              :value="value"
              size="32rpx"
            />
            <div class="distance">
                <p>距离：1.57KM</p>
                <p class="openTime">8:00-18:00</p>
                <span class="store-type">配送中</span>
            </div>
        </div>
    </div>
    <div class="goods-container">
        <div class="goods-header">
            <img class="fireIcon" src="../../../static/images/fire.png" alt="">
            <span>热销水饮</span>
        </div>
        <!-- <div class="goods-items">
            <div class="goods-item">
                <img class="goodsImg" src="https://mp.weixin.qq.com/cgi-bin/showqrcode?ticket=gQGm8DwAAAAAAAAAAS5odHRwOi8vd2VpeGluLnFxLmNvbS9xLzAyY2lrelJuTG5lRjMxMDAwMDAwM3YAAgRLmEFcAwQAAAAA" alt="">
                <p>桶装水</p>
            </div>
            <div class="goods-item">
                <img class="goodsImg" src="https://mp.weixin.qq.com/cgi-bin/showqrcode?ticket=gQGm8DwAAAAAAAAAAS5odHRwOi8vd2VpeGluLnFxLmNvbS9xLzAyY2lrelJuTG5lRjMxMDAwMDAwM3YAAgRLmEFcAwQAAAAA" alt="">
                <p>桶装水</p>
            </div>
            <div class="goods-item">
                <img class="goodsImg" src="https://mp.weixin.qq.com/cgi-bin/showqrcode?ticket=gQGm8DwAAAAAAAAAAS5odHRwOi8vd2VpeGluLnFxLmNvbS9xLzAyY2lrelJuTG5lRjMxMDAwMDAwM3YAAgRLmEFcAwQAAAAA" alt="">
                <p>桶装水</p>
            </div>
            <div class="goods-item">
                <img class="goodsImg" src="https://mp.weixin.qq.com/cgi-bin/showqrcode?ticket=gQGm8DwAAAAAAAAAAS5odHRwOi8vd2VpeGluLnFxLmNvbS9xLzAyY2lrelJuTG5lRjMxMDAwMDAwM3YAAgRLmEFcAwQAAAAA" alt="">
                <p>桶装水</p>
            </div>
        </div> -->
        
          <card :cardInfo=cardInfo></card>
        
        <shopInfo></shopInfo>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'
import shopInfo from '@/components/shopInfo'
export default {
  data() {
    return {
      value:3,
      cardInfo:[
        {
          "name":"农夫山泉饮用水天然水5L*4两箱装",
          "imageUrl":'http://img5.imgtn.bdimg.com/it/u=1204418728,4083752615&fm=26&gp=0.jpg',
          "desc":"我们不生产水，只是大自然的搬运工",
          "price":72
        },{
          "name":"农夫山泉饮用水天然水5L*2",
          "imageUrl":'http://img2.imgtn.bdimg.com/it/u=3582660187,1737712283&fm=26&gp=0.jpg',
          "desc":"我们不生产水，只是大自然的搬运工",
          "price":38
        },{
          "name":"农夫山泉饮用水天然水5L",
          "imageUrl":'http://img0.imgtn.bdimg.com/it/u=3484443056,3637330532&fm=26&gp=0.jpg',
          "desc":"我们不生产水，只是大自然的搬运工",
          "price":20
        },{
          "name":"农夫山泉饮用水天然水5L",
          "imageUrl":'http://img5.imgtn.bdimg.com/it/u=1204418728,4083752615&fm=26&gp=0.jpg',
          "desc":"我们不生产水，只是大自然的搬运工",
          "price":20
        },{
          "name":"农夫山泉饮用水天然水5L",
          "imageUrl":'http://img0.imgtn.bdimg.com/it/u=3484443056,3637330532&fm=26&gp=0.jpg',
          "desc":"我们不生产水，只是大自然的搬运工",
          "price":20
        },  
      ]
    };
  },
  methods: {
  },
  components: {
    card,
    shopInfo
  },
};
</script>
<style lang='scss' scoped>
.shop-container{
  display: flex;
  height: 100vh;
  flex-direction: column;
  background: #fff;
  padding: 40rpx 20rpx 0;
}
.shop-header{
  display: flex;
  padding: 20rpx 20rpx;
  background:#fff;
  .shopImg{
    position: relative;
    top: -40rpx;
    width: 120rpx;
    height: 120rpx;
    padding: 16rpx;
    background: #fff;
    display: flex;
    img{
      width: 100%;
      height: 100%;
    }
  }
  .shopIofo{
    flex:1;
    display: flex;
    flex-direction: column;
    margin-left: 20rpx;
    h2{
      font-size: 32rpx;
      color: #000;
      font-weight: 600;
    }
    .distance{
      display: flex;
      p{
        font-size: 22rpx;
        color: #333;
        padding-right:20rpx; 
        margin-bottom: 0;
      }
      .openTime{
        padding-left: 20rpx;
      }
      .store-type{
        display: inline-block;
        margin-left: 20rpx;
        width: 120rpx;
        height: 40rpx;
        text-align: center;
        line-height:40rpx;
        background-color: #D6BA8B;
        border-radius: 20rpx;
        color: #fff;
        font-size: 24rpx;
      }
    }
  }
}
.goods-container{
  margin-top: 10rpx;
  .goods-header{
    display: flex;
    align-items: center;
    border-bottom: 1rpx solid #DFE4E8;
    margin-bottom: 20rpx;
    .fireIcon{
      width: 50rpx;
      height: 50rpx;
    }
    span{
      margin-left: 20rpx;
      font-size: 26rpx;
    }
  }
}
// .goods-items{
//   display: flex;
//   flex-direction: row;
//   justify-content: space-between;
// }
// .goods-item{
//   display: flex;
//   flex-direction: column;
//   width: 20%;
//   align-items: center;
//   padding: 0 10rpx;
//   p{
//     font-size: 14rpx;
//   }
// }
// .goodsImg{
//   width: 170rpx;
//   height: 150rpx;
//   margin-bottom: 10rpx;
// }

</style>

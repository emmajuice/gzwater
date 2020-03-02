<template>
  <div class="goods">
    <div class="swiper">
      <swiper class="swiper-container" indicator-dots="true" autoplay="true" interval="3000" duration="1000">
        <block>
          <swiper-item class="swiper-item">
            <image src="https://www.mywhh.com/images/201801/thumb_img/14_thumb_G_1516738724687.jpg" class="slide-image" />
          </swiper-item>
          <swiper-item class="swiper-item">
            <image src="https://www.mywhh.com/images/201801/thumb_img/55_thumb_G_1516830146816.jpg" class="slide-image" />
          </swiper-item>
        </block>
      </swiper>
      <button class="share" hover-class="none" open-type="share" value="">分享商品</button>
    </div>
    <div class="swiper-b">
      <div class="item">30天无忧退货</div>
      <div class="item">48小时快速退款</div>
      <div class="item">满88元免邮费</div>
    </div>
    <div class="goods-info">
      <div class="c">
        <p>桶装纯净水8L一桶</p>
        <p>我们不生产水 我们只是大自然的搬运工</p>
        <p>￥14</p>
        <div class="brand">
          <p>农夫山泉</p>
        </div>
      </div>
    </div>
    <!-- <div @click="showType" class="section-nav">
      <div>请选择规格数量</div>
      <div></div>
    </div> -->
    <!-- <div @click="showType" class="section-nav">
      <div>用户评价</div>
      <div></div>
    </div> -->

    <!-- <div v-if="attribute.length!=0" class="attribute">
      <div class="head">
        商品参数
      </div>
      <div class="item">
        <div>.name</div>
        <div>tem.value</div>
      </div>
      <div class="item">
        <div>.name22</div>
        <div>tem.value</div>
      </div>
      <div class="item">
        <div>.name33</div>
        <div>tem.value</div>
      </div>
    </div> -->
    <!-- <div v-if="goods_desc" class="detail">
      <wxParse :content="goods_desc" />
    </div> -->
    <!-- 常见问题 -->
    <!-- <div class="common-problem">
      <div class="h">
        <div class="line"></div>
        <text class="title">常见问题</text>
        <div class="line"></div>
      </div>
      <div class="b">
        <div class="item">
          <div class="question-box">
            <text class="spot"></text>
            <text class="question">wentiquestion</text>
          </div>
          <div class="answer">
            buzdhi
          </div>
        </div>
        <div class="item">
          <div class="question-box">
            <text class="spot"></text>
            <text class="question">wentiquestion</text>
          </div>
          <div class="answer">
            buzdhi
          </div>
        </div>
      </div>
    </div> -->
    <!-- 常见问题 -->
    <!-- 大家都在看 -->

    <!-- <div class="common-problem">
      <div class="h">
        <div class="line"></div>
        <text class="title">大家都在看</text>
        <div class="line"></div>
      </div>
      <div class="sublist">
        <div @click="togoodsDetail">
          <img src="http://img5.imgtn.bdimg.com/it/u=1204418728,4083752615&fm=26&gp=0.jpg" alt="">
          <p>sjksjjsj</p>
          <p>￥66.2</p>
        </div>
      </div>
    </div> -->

    <!-- 大家都在看 -->
    <!-- <div class="bottom-fixed">
      <div @click="collect">
        <div class="collect" :class="[collectFlag ? 'active' :'']">

        </div>

      </div>
      <div @click="toCart">
        <div class="car">
          <span>
            {{allnumber}}
          </span>
          <img src="http://img5.imgtn.bdimg.com/it/u=1204418728,4083752615&fm=26&gp=0.jpg" alt="">
        </div>
      </div>
      <div @click="bug">立即购买</div>
      <div @click="addCart">加入购物车</div>
    </div> -->

    <!-- 选择规格部分 -->
    <!-- <div v-show="showpop" @click="showType" class="pop">

    </div>
    <div class="attr-pop" :class="[showpop ? 'fadeup' : 'fadedown']">
      <div class="top">
        <div class="left">
          <img src="http://img5.imgtn.bdimg.com/it/u=1204418728,4083752615&fm=26&gp=0.jpg" alt="">
        </div>
        <div class="right">
          <div>
            <p>价格￥123</p>
            <p>请选择数量</p>
          </div>
        </div>
        <div @click="showType" class="close">
          X
        </div>
      </div>
      <div class="b">
        <p>数量</p>
        <div class="count">
          <div @click="reduce" class="cut">-</div>
          <input class="number" disabled="" v-model="number" />
          <div @click="add" class="add">+</div>
        </div>
      </div>
    </div> -->

    <!-- 选择规格部分 -->
  </div>
</template>

<script>
// import { get, post, toLogin, login, getStorageOpenid } from "../../utils";
// import wxParse from "mpvue-wxparse";

export default {
  onShow() {
  },
  mounted() {
    //判断是否登录获取用户信息
    // if (login()) {
    //   this.userInfo = login();
    // }
    // console.log(this.$root.$mp.query.id);

    // this.id = this.$root.$mp.query.id;

    // this.openId = getStorageOpenid();
    // this.goodsDetail();
  },
  //商品转发
  onShareAppMessage() {
    console.log(this.info.name);
    console.log(this.info.id);
    console.log(this.gallery[0].img_url);

    return {
      title: this.info.name,
      path: "/pages/goods/main?id=" + this.info.id
    };
  },
  data() {
    return {
      allnumber: 0,
      openId: "",
      collectFlag: false,
      number: 0,
      showpop: false,
      gallery: [],
      info: {},
      brand: {},
      attribute: [],
      issueList: [],
      productList: [],
      goods_desc: "",
      id: "",
      userInfo: "",
      goodsId: "",
      allPrise: ""
    };
  },
  // components: {
  //   wxParse
  // },
  methods: {
    togoodsDetail(id) {
      wx.redirectTo({ url: "/pages/goods/main?id=" + id });
    },
    add() {
      this.number = this.number + 1;
    },
    reduce() {
      if (this.number > 1) {
        this.number = this.number - 1;
      } else {
        return false;
      }
    },
    // async bug() {
    //   if (toLogin()) {
    //     if (this.showpop) {
    //       if (this.number == 0) {
    //         wx.showToast({
    //           title: "请选择商品数量", //提示的内容,
    //           duration: 2000, //延迟时间,
    //           icon: "none",
    //           mask: true, //显示透明蒙层，防止触摸穿透,
    //           success: res => { }
    //         });
    //         return false;
    //       }
    //       console.log(this.goodsId);
    //       console.log(this.openId);

    //       // const data = await post("/order/submitAction", {
    //       //   goodsId: this.goodsId,
    //       //   openId: this.openId,
    //       //   allPrise: this.allPrise
    //       // });
    //       if (data) {
    //         wx.navigateTo({
    //           url: "/pages/order/main"
    //         });
    //       }
    //     } else {
    //       this.showpop = true;
    //     }
    //   }
    // },
    async collect() {
      if (toLogin()) {
        this.collectFlag = !this.collectFlag;
        // const data = await post("/collect/addcollect", {
        //   openId: this.userInfo.openId,
        //   goodsId: this.goodsId
        // });
      }
    },
    async addCart() {
      if (toLogin()) {
        if (this.showpop) {
          if (this.number == 0) {
            wx.showToast({
              title: "请选择商品数量", //提示的内容,
              duration: 2000, //延迟时间,
              icon: "none",
              mask: true, //显示透明蒙层，防止触摸穿透,
              success: res => { }
            });
            return false;
          }
          const data = await post("/cart/addCart", {
            openId: this.userInfo.openId,
            goodsId: this.goodsId,
            number: this.number
          });
          //添加成功后
          if (data) {
            this.allnumber = this.allnumber + this.number;
            wx.showToast({
              title: "添加购物车成功",
              icon: "success",
              duration: 1500
            });
          }
        } else {
          this.showpop = true;
        }
      }
    },
    toCart() {
      wx.switchTab({
        url: "/pages/cart/main"
      });
      // wx.navigateTo({
      //   url: "/pages/cart/main"
      // });
    },
   
    showType() {
      this.showpop = !this.showpop;
    }
  },
  computed: {}
};
</script>
<style lang='scss' scoped>
.goods {
  overflow: hidden;

  .swiper {
    width: 750rpx;
    height: 750rpx;
    position: relative;

    .swiper-container {
      width: 750rpx;
      height: 750rpx;

      image {
        width: 750rpx;
        height: 750rpx;
      }
    }

    .share {
      position: absolute;
      border-radius: 40rpx 0 0 40rpx;
      width: 150rpx;
      height: 65rpx;
      line-height: 65rpx;
      text-align: center;
      right: 0;
      top: 50rpx;
      background: #e0a354;
      color: #fff;
      font-size: 24rpx;
    }
  }

  .swiper-b {
    width: 710rpx;
    height: 73rpx;
    margin: 0 auto;
    background: #f4f4f4; // padding: 0 31.25rpx;
    display: flex;
    align-items: center;
    justify-content: space-between;

    div {
      background: url('http://nos.netease.com/mailpub/hxm/yanxuan-wap/p/20150730/style/img/icon-normal/servicePolicyRed-518d32d74b.png') 0 center no-repeat;
      background-size: 10rpx;
      padding-left: 15rpx;
      display: flex;
      align-items: center;
      font-size: 25rpx;
      color: #666;
    }
  }

  .goods-info {
    width: 750rpx;
    height: 306rpx;
    background: #fff;
    margin: 0 auto;
    border-bottom: 1rpx solid #f4f4f4;

    .c {
      height: 100%;

      p {
        display: block;
        text-align: center;
      }

      p:nth-child(1) {
        font-size: 41rpx;
        padding: 20rpx;
      }

      p:nth-child(2) {
        margin-bottom: 25rpx;
        font-size: 24rpx;
        color: #999;
      }

      p:nth-child(3) {
        margin-top: 10rpx;
        font-size: 35rpx;
        color: #b4282d;
      }

      .brand {
        margin-top: 25rpx;
        text-align: center;

        p {
          display: inline-block;
          color: #b1a279;
          font-size: 20rpx;
          padding: 5rpx 30rpx;
          border: 1rpx solid #b1a279;
        }
      }
    }
  }

  .section-nav {
    height: 108rpx;
    background: #fff;
    margin-bottom: 20rpx;
    padding: 0 20rpx;
    display: flex;
    justify-content: space-between;
    align-items: center;

    div:nth-child(2) {
      width: 52rpx;
      height: 52rpx;
      background: pink;
      background-size: 100% 100%;
    }
  }

  .attribute {
    padding: 20rpx 30rpx;
    background: #fff;
    margin-bottom: 20rpx;

    .head {
      font-size: 38rpx;
      padding: 20rpx 0;
    }

    .item {
      display: flex;
      background: #f7f7f7;
      padding: 20rpx 0;
      margin: 20rpx;

      div:nth-child(1) {
        width: 134rpx;
        font-size: 25rpx;
        color: #999;
      }

      div:nth-child(2) {
        flex: 1;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  }

  .common-problem {
    margin-bottom: 110rpx;

    .h {
      padding: 35rpx 0;
      background: #fff;
      text-align: center;
      display: flex;
      align-items: center;
      justify-content: center;

      .line {
        display: inline-block;
        height: 1rpx;
        width: 100rpx;
        background: #ccc;
      }

      .title {
        padding: 0 25rpx;
        background: #fff;
      }
    }

    .b {
      padding: 0rpx 30rpx;
      background: #fff;

      .item {
        padding-bottom: 25rpx;

        .question-box {
          display: flex;

          .spot {
            height: 8rpx;
            width: 8rpx;
            background: #b4282d;
            border-radius: 50%;
            margin-top: 11rpx;
          }

          .question {
            line-height: 30rpx;
            padding-left: 8rpx;
            display: block;
            font-size: 26rpx;
            padding-bottom: 15rpx;
            color: #303030;
          }
        }

        .answer {
          line-height: 40rpx;
          padding-left: 16rpx;
          font-size: 26rpx;
          color: #787878;
        }
      }
    }

    .sublist {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      width: 730rpx;
      margin: 0 auto;

      div {
        width: 360rpx;
        background: #fff;
        margin-bottom: 10rpx;
        padding-bottom: 10rpx;

        img {
          display: block;
          width: 302rpx;
          height: 302rpx;
          margin: 0 auto;
        }

        p {
          margin-bottom: 5rpx;
          text-indent: 1em;
        }

        p:nth-child(2) {
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
          width: 98%;
        }

        p:nth-child(3) {
          color: #9c3232;
        }
      }

      .last {
        display: block;
        width: 302rpx;
        height: 302rpx;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;

        p {
          height: 33rpx;
          width: 100%;
          line-height: 33rpx;
          color: #333;
          font-size: 33rpx;
          text-align: center;
        }

        .icon {
          display: inline-block;
          width: 70rpx;
          height: 70rpx;
          background: yellowgreen;
          background-size: 100% 100%;
          margin-top: 60rpx;
        }
      }

      div:nth-child(2n) {
        margin-left: 10rpx;
      }
    }
  }

  .pop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
  }

  .attr-pop {
    position: fixed;
    width: 100%;
    height: 500rpx;
    bottom: -500rpx;
    transition: all 400ms ease;
    box-sizing: border-box;
    padding: 30rpx;
    background: #fff;

    .top {
      display: flex;
      margin-bottom: 35rpx;
      position: relative;

      .close {
        position: absolute;
        right: 0;
        top: 0px;
        font-size: 30rpx;
        color: #999;
      }

      .left {
        height: 177rpx;
        width: 177rpx;
        margin-right: 30rpx;

        img {
          float: left;
          height: 177rpx;
          width: 177rpx;
        }
      }

      .right {
        flex: 1;
        display: flex;
        align-items: flex-end;

        p {
          width: 100%;
          line-height: 45rpx;
        }

        p:nth-child(1) {
          color: #b4282d;
        }
      }
    }

    .b {
      .count {
        width: 322rpx;
        height: 71rpx;
        line-height: 71rpx;
        display: flex;
        border: 1rpx solid #ccc;
        margin-top: 20rpx;

        div {
          width: 90rpx;
          text-align: center;
        }

        input {
          flex: 1;
          height: 100%;
          text-align: center;
          border-left: 1rpx solid #ccc;
          border-right: 1rpx solid #ccc;
        }
      }
    }
  }

  .fadeup {
    transform: translateY(-500rpx); // transition: all 0.4s ease;
  }

  .bottom-fixed {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    width: 750rpx;
    height: 100rpx;
    display: flex;
    background: #fff;
    z-index: 10;

    div:nth-child(1) {
      height: 100rpx;
      width: 162rpx;
      border: 1rpx solid #f4f4f4;
      display: flex;
      align-items: center;
      justify-content: center;

      .collect {
        display: block;
        height: 44rpx;
        width: 44rpx;
        background: skyblue;
        background-size: 100% 100%;
      }

      .collect.active {
        display: block;
        height: 44rpx;
        width: 44rpx;
        background: orange;
        background-size: 100% 100%;
      }
    }

    div:nth-child(2) {
      height: 100rpx;
      width: 162rpx;
      border: 1rpx solid #f4f4f4;
      display: flex;
      align-items: center;
      justify-content: center;

      .car {
        position: relative;
        height: 60rpx;
        width: 60rpx;

        span {
          height: 28rpx;
          width: 28rpx;
          z-index: 10;
          position: absolute;
          top: 0;
          right: 0;
          background: #b4282d;
          text-align: center;
          font-size: 18rpx;
          color: #fff;
          line-height: 28rpx;
          border-radius: 50%;
        }

        img {
          display: block;
          height: 44rpx;
          width: 44rpx;
          position: absolute;
          top: 10rpx;
          left: 0;
        }
      }
    }

    div:nth-child(3) {
      height: 100rpx;
      line-height: 96rpx;
      flex: 1;
      text-align: center;
      color: #333;
      border-top: 1rpx solid #f4f4f4;
      border-bottom: 1rpx solid #f4f4f4;
    }

    div:nth-child(4) {
      border: 1rpx solid #b4282d;
      background: #b4282d;
      float: left;
      height: 100rpx;
      line-height: 96rpx;
      flex: 1;
      text-align: center;
      color: #fff;
    }
  }
}

</style>

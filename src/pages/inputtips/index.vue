<template>
  <div>
    <div class="section">
      <input @input="bindInput" placeholder="搜索" focus="true" />
    </div>
    <div @touchstart="bindSearch" :data-keywords="item.name" class="text_box" v-for="(item,index) in tips" :key="index">
      {{item.name}}
    </div>
  </div>
</template>
 
<script>
import amapFile from '../../libs/amap-wx.js'
import config from '../../libs/config.js'
var lonlat;
var city;
export default {
  data () {
    return {
      tips: []
    }
  },
  onLoad: function(e){
    lonlat = e.lonlat;
    city = e.city;
  },
  methods: {
    bindInput: function(e){
      console.log("bindInput",e)
    var that = this;
    var keywords = e.mp.detail.value; 
    var key = config.Config.key;
    var myAmapFun = new amapFile.AMapWX({key: key});
    myAmapFun.getInputtips({
      keywords: keywords,
      location: lonlat,
      city: city,
      success: function(data){
        if(data && data.tips){
          that.tips = data.tips;
        }
      }
    })
  },
  bindSearch: function(e){
    console.log("bindSearch",e)
    var keywords = e.target.dataset.keywords;
    console.log("keywords",keywords)
    let url = '../home/main?keywords=' + keywords;
    let url1 = '../home/main';
    console.log("url======",url1,url)
    wx.redirectTo({
      url: url
    })
    
  }
  }
}
</script>
 
<style scoped>
.section{
  height: 30px;
  width: 100%;
}
.section input{
  width:90%;
  margin:5px auto;
  border:1px solid #c3c3c3;
  height:30px;
  border-radius: 3px;
  padding: 0 5px;
}
.text_box{
  margin: 10px 25px;
  border-bottom:1px solid #c3c3c3;
  padding-bottom:10px
}
</style>

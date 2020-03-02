<template>
  <div>   
    首页
    
  </div>
</template>
 
<script>
import amapFile from '../../libs/amap-wx.js'
import config from '../../libs/config.js'
var markersData = [];
export default {
  data () {
    return {
      markers: [],
      latitude: '',
      longitude: '',
      textData: {},
      city: ''
    }
  },
  beforeMount(e) {
    var that = this;
    var key = config.Config.key;
    var myAmapFun = new amapFile.AMapWX({key: key});
    var params = {
      iconPathSelected: '../../static/images/marker_checked.png',
      iconPath: '../../static/images/marker.png',
      success: function(data){
        // console.log("data",data)
        markersData = data.markers;
        var poisData = data.poisData;
        var markers_new = [];
        markersData.forEach(function(item,index){
          markers_new.push({
            id: item.id,
            latitude: item.latitude,
            longitude: item.longitude,
            iconPath: item.iconPath,
            width: item.width,
            height: item.height
          })

        })
        // console.log("markersData",markersData)
        if(markersData.length > 0){
          that.markers = markers_new;
          that.city = poisData[0].cityname || '';
          that.latitude = markersData[0].latitude;
          that.longitude = markersData[0].longitude;
          that.showMarkerInfo(markersData,0);
        }else{
          wx.getLocation({
            type: 'gcj02',
            success: function(res) {
              that.latitude = res.latitude;
              that.longitude = res.longitude;
              that.city = '贵阳市';
            },
            fail: function(){
              that.latitude = 26.646769;
              that.longitude = 106.631049;
              that.city = '贵阳市';
            }
          })
          
          that.textData ={
              name: '抱歉，未找到结果',
              desc: ''
            };
        }
        
      },
      fail: function(info){
        wx.showModal({title:info.errMsg})
      }
    }
    if(e && e.keywords){
      console.log("params=======",params,e);
      params.querykeywords = e.keywords;
    }
    myAmapFun.getPoiAround(params)
  },
  methods: {
    handlecilck(){
      console.log("i am here")
    },
    bindInput(e){
      var that = this;
      var url = '../inputtips/main';
      if(e.target.dataset.latitude && e.target.dataset.longitude && e.target.dataset.city){
        var dataset = e.target.dataset;
        url = url + '?lonlat=' + dataset.longitude + ',' + dataset.latitude + '&city=' + dataset.city;
      }
      console.log("url00000======",url)
      wx.redirectTo({
        url: url
      })
    },
    showMarkerInfo: function(data,i){
      var that = this;
      that.textData= {
          name: data[i].name,
          desc: data[i].address
        };
    },
    changeMarkerColor: function(data,i){
      console.log(data,i)
      var that = this;
      var markers = [];
      for(var j = 0; j < data.length; j++){
        if(j==i){
          data[j].iconPath = "../../static/images/marker_checked.png";
        }else{
          data[j].iconPath = "../../static/images/marker.png";
        }
        markers.push({
          id: data[j].id,
          latitude: data[j].latitude,
          longitude: data[j].longitude,
          iconPath: data[j].iconPath,
          width: data[j].width,
          height: data[j].height
        })
      }
      that.markers= markers;
    }
    },
    makertap: function(e) {
      console.log("dfjksdlj",e)
      var id = e.markerId;
      var that = this;
      that.showMarkerInfo(markersData,id);
      that.changeMarkerColor(markersData,id);
    },
    test(){
      console.log("jsdljfklsdjfklsdjlf")
    },
    play1(){  
                console.log(11111);  
            },

  }
</script>
 
<style lang="scss" scoped>
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
.map_container{
  margin-top: 10rpx;
}
.map{
  width: 100%;
  height: 600rpx;
}
.map_text{
  margin-top: 10rpx;
  background: #ffffff;
  padding: 0 15px;
  border-bottom: 1px solid #ccc;
  p{
    margin: 5px 0;
    display: block;
    font-size:12px;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden; 
  }
  .testBtn{
    background: orange;
  }
  .name{
    font-size:28rpx;
    font-weight: 600;    
  }
}
</style>
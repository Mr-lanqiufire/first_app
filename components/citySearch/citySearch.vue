<template>
	<view class="content clearfix">
		<view class="left fl">
      <scroll-view scroll-y :scroll-into-view="a" :scroll-with-animation="true">
        <view class="cityTop">
            <view id="add" class="nowCity p20 fz_30 border_bottom">当前:上海</view>
            <view class="lately p20 fz_30">定位/最近访问</view>
            <view class="lately_children p20"></view>
            <view id="ahot" class="fz_30 p20">热门城市</view>
            <view class="hots tc border_bottom p_bottom" v-for="(item,itemIndex) in cityAll" v-if="item.title=='热门城市'" :key="item.type">
              <view class="hotCity" v-for="(it,itIndex) in item.item" :key="it.key">{{it.name}}</view>
            </view>
        </view>
        <view class="allCity p20">所有城市</view>
        <view class="allCityList" v-for="(item,itemIndex) in cityAll" :key="item.title" v-if="item.title!='热门城市'">
          <view :id="'a'+item.title" class="cityTitle ">{{item.title}}</view>
          <view class="everyCity m20 border_bottom p10" v-for="(it,itIndex) in item.item" :key="it.key">{{it.name}}</view>
        </view>
      </scroll-view>
		</view>
		<view class="right p20 fz_25" >
			<view class="add" v-for="(item,index) in cityTitle" :key="item" @touchstart="touchStart($event)" @touchmove="touchMove($event)"  @touchend="touchEnd($event)" :data-item="item">{{item}}</view>
			<view class="tipTap" :hidden="orHidden">{{tipTap}}</view>
		</view>
	</view>
</template>

<script>
	import city from "../../static/util/allcity.js"
	export default {
		data() {
			return {
				cityTitle:["当前","热门","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"],
				cityAll:city,
				tipTap:"",
				orHidden:true,
        a:null,
        ch:null,
        fa:null
			};
		},
    
		mounted(){
			this.getaa()
			
		},
		methods:{
      getaa(){
        let self=this;
        wx.createSelectorQuery().select('.add').boundingClientRect(function (rect) {
            // console.log(rect.height)
          self.ch=rect.height;
        }).exec() ;
          // console.log(rect.height)
        wx.createSelectorQuery().select('.right').boundingClientRect(function (rect) {
            // console.log(rect.height)
          self.fa=rect.height;
        }).exec() 
          // console.log(this.fa,this.ch)
      },
			touchStart(e){
				// console.log(e,111)
         console.log(this.fa,this.ch)
				this.tipTap=e.currentTarget.dataset.item;
         if(e.currentTarget.dataset.item=="当前"){
           e.currentTarget.dataset.item="dd"
         }else if(e.currentTarget.dataset.item=="热门"){
           e.currentTarget.dataset.item="hot"
         }
				// console.log(e.currentTarget.dataset.item)
				this.orHidden=false;
        this.a="a"+e.currentTarget.dataset.item;
			},
			touchMove(e){
        console.log(this.fa,this.ch)
        let num=Math.round(this.fa/this.ch);
        console.log(num);
        this.tipTap=this.cityTitle[num];
        this.a="a"+e.currentTarget.dataset.item;
      },
			touchEnd(e){
				console.log(e)
				let self=this;
				let timer=setTimeout(function(){
					self.orHidden=true;
					clearTimeout(timer);
				},500)
			}
		}
	}
</script>

<style scoped>
	.content{width: 100%;height: 100%;}
	.nowCity,.lately{width:100%;}
	.lately_children{width: 100%;height: 60upx;}
	.left{width: calc(100% - 60upx);height: 100%;}
  scroll-view{width: 100%;height: 100%;}
	.cityTop{width: 100%;padding: 0 20upx;}
	.right{width: 60upx;background-color: #F3F3F3;height: 100%;display: flex;flex-direction: column;align-items:center;justify-content: space-around;
			position: fixed;right: 0;top: 0;}
	.hots{width: 100%;display: flex;justify-content: space-between;flex-wrap:wrap;}
	.hotCity{width: 30%;height: 60upx;border: 2upx solid #ccc;margin-top: 15upx;border-radius: 10upx;}
	.border_bottom{border-bottom: 2upx solid #F1F1F1;}
	.p20{padding: 20upx 0;}
	.p10{padding: 10upx 0;}
	.p_bottom{padding-bottom: 30upx;}
	.allCity{padding-left: 20upx;}
	/* .allCityList{padding-right: 20upx;} */
	.cityTitle{width: 100%;height:50upx;background-color: #EAEAEA;padding-left: 20upx;}
	.m20{margin:0 20upx;}
	.everyCity{}
	.tipTap{position:absolute;left:-110upx;top:0;width: 100upx;height:70upx;border: 1upx solid #ccc;}
</style>

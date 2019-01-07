<template>
	<view class="content clearfix">
		<view class="left fl">
			<view class="cityTop">
				<view class="nowCity p20 fz_30 border_bottom">当前:上海</view>
				<view class="lately p20 fz_30">定位/最近访问</view>
				<view class="lately_children p20"></view>
				<view class="fz_30 p20">热门城市</view>
				<view class="hots tc border_bottom p_bottom" v-for="(item,itemIndex) in cityAll" v-if="item.title=='热门城市'" :key="item.type">
					<view class="hotCity"  v-for="(it,itIndex) in item.item" :key="it.key">{{it.name}}</view>
				</view>
			</view>
			<view class="allCity p20">所有城市</view>
			<view class="allCityList" v-for="(item,itemIndex) in cityAll" :key="item.title" v-if="item.title!='热门城市'">
				<view class="cityTitle ">{{item.title}}</view>
				<view class="everyCity m20 border_bottom" v-for="(it,itIndex) in item.item" :key="it.key">{{it.name}}</view>
			</view>
		</view>
		<view class="right p20 fr fz_25">
			<view v-for="(item,index) in cityTitle" :key="item">{{item}}</view>
		</view>
	</view>
</template>

<script>
	import city from "../../static/util/allcity.js"
	export default {
		data() {
			return {
				cityTitle:["当前","热门","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"],
				cityAll:city
			};
		},
		mounted(){
			console.log(city)
		}
	}
</script>

<style scoped>
	.content{width: 100%;height: 100%;}
	.nowCity,.lately{width:100%;}
	.lately_children{width: 100%;height: 60upx;}
	.left{width: calc(100% - 50upx);}
	.cityTop{width: 100%;padding: 0 20upx;}
	.right{width: 50upx;background-color: #F3F3F3;height: 100%;display: flex;flex-direction: column;align-items:center;justify-content: space-around;}
	.hots{width: 100%;display: flex;justify-content: space-between;flex-wrap:wrap;}
	.hotCity{width: 30%;height: 60upx;border: 2upx solid #ccc;margin-top: 15upx;border-radius: 10upx;}
	.border_bottom{border-bottom: 2upx solid #ccc;}
	.p20{padding: 20upx 0;}
	.p_bottom{padding-bottom: 30upx;}
	.allCity{padding-left: 20upx;}
	.cityTitle{width: 100%;height:50upx;background-color: #E6E6E6;padding-left: 20upx;}
	.m20{margin: 0 20upx;}
</style>

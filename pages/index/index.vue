<template>
	<view class="content ">
		<view class="header d_fl a_c ">
			<view class="location fl">
				<view class="locationName fz_26">上海海边沙子上的蚂蚁</view>
				<uni-icon type="arrowdown" size="15"></uni-icon>
			</view>
			<!-- <uni-drawer :visible="draw" :mask="true" mode="left">
				<view style="padding:30upx;">
					<view class="uni-title">抽屉式导航</view>
					<button>这是按钮</button>
				</view>
			</uni-drawer> -->
			<view class="input fr">
				<view class="search">
					<image src="../../static/images/search.png" mode=""></image>
				</view>
				<input type="text" placeholder="请输入商家名、品类或者商圈..." placeholder-class="fz_26 c_999"></view>
		</view>
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" :circular="true">
			<swiper-item v-for="(item,index) in imgs" :key="index" :class="'aa'+index">
				<view class="swiper-item">{{item}}</view>
			</swiper-item>
		</swiper>
		<view class="types d_fl">
			<view v-for="(item,index) in types" :id="index" :key="index"  class="tc">
				<view class="bg_cc d_fl a_c j_c" @tap="goFenLei">
					<image :src="item.src" mode=""></image>
				</view>
				<text class="fz_25">{{item.name}}</text>
			</view>
		</view>
		
		
	</view>
</template>
<script>
	import uniDrawer from "@/components/uni-drawer/uni-drawer.vue";
	import uniIcon from "@/components/uni-icon/uni-icon.vue";
	export default {
		components:{
			uniDrawer,
			uniIcon
		},
		data() {
			return {
				title: 'Hello',
				login:'登录',
				imgs:[1,2,3],
				types:[
					{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},{
						name:'酒店',
						src:'../../static/images/jiudian.png'
					},
				],
				draw:false
			}
		},
		onLoad() {

		},
		methods: {
			goFenLei(e){
				console.log(e);
				console.log(e.currentTarget.id);
				// debugger
				if(e.currentTarget.id=="9"){
					console.log("I`m come in")
					uni.navigateTo({
						url:"/pages/index/shoppingTypes"
					})
				}
			},
			changeDraw(){
				this.draw=!this.draw;
			}
		}
	}
</script>

<style>
	.header{width:100%;height: 80upx;background-color:#fff;padding: 10upx 20upx;justify-content: space-around;}
	.menu{width: 40upx;height: 40upx;margin:0 15upx;}
	swiper{padding: 15upx;}
	.input{width: calc(100% - 180upx);height: 100%;position: relative;}
	.search{width:45upx;height: 45upx;position: absolute;top: 9upx;left: 25upx;}
	.location{display: flex;justify-content: space-around;align-items: center;}
	.locationName{width:80upx;height: 100%;text-overflow: ellipsis;white-space: nowrap;overflow: hidden;}
	.aa0{width: 100%;height: 400upx;background-color: #ccc;}
	.aa1{width: 100%;height: 400upx;background-color: #ff00ff;}
	.aa2{width: 100%;height: 400upx;background-color: #00ffff;}
	.header>view>input{height: 100%;background-color: #E3E4E3;border-radius: 30upx;padding-left: 70upx;}
	.bg_cc{width:100upx;height: 100upx;background-color: #ccc;margin: 0 15upx 0;border-radius: 50%;}
	.types{display: flex;flex-flow: row wrap;align-content: flex-start;justify-content: space-between;padding:20upx;}
	image{width: 60%;height: 60%;}
</style>

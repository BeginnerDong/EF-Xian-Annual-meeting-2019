<template>
	<view>
		<view class="indexBJ" style=""></view>
		
		<view class="indexNav center flexRowBetween">
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/Seat-mySeat/Seat-mySeat'}})">
				<view><image class="icon" src="../../static/images/icon5.png" mode=""></image></view>
				<view class="title">我的座位</view>
				<view class="text">my seating arrangement</view>
			</view>
			<view class="item" @click="Router.navigateTo({route:{path:'/pages/details/details?name=桌位分布'}})">
				<view><image class="icon" src="../../static/images/icon4.png" mode=""></image></view>
				<view class="title">桌位分布</view>
				<view class="text" style="width: 120rpx;">table plan</view>
			</view>
		</view>
		
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				Router:this.$Router,
				showView: false,
				wx_info:{},
				is_show:false
			}
		},
		onLoad() {
			const self = this;
			// self.$Utils.loadAll(['getMainData'], self);
		},
		methods: {
			getMainData() {
				const self = this;
				console.log('852369')
				const postData = {};
				postData.tokenFuncName = 'getProjectToken';
				self.$apis.orderGet(postData, callback);
			}
		}
	};
</script>

<style>
	/* @import "../../assets/style/navbar.css"; */
	.indexBJ{width: 100%;height: 100%;background: url(../../static/images/img.jpg) no-repeat 0 0 /100% 100%;position: fixed;top: 0;right: 0; bottom: 0;left: 0;}
	
	.indexNav{flex-wrap: wrap;align-items: flex-start;position: relative;z-index: 2;width: 100%;box-sizing: border-box;padding: 75% 8% 0 8%;}
	.indexNav .item{width: 50%;}
	.indexNav .item .icon{width: 80rpx;height: 80rpx;display: block;margin: 0 auto;}
	.indexNav .item .title{font-size: 30rpx;font-weight: bold;padding: 20rpx 0 14rpx 0;}
	.indexNav .item .text{width: 170rpx;font-size: 24rpx;color: #4e4a49;text-transform:uppercase;margin: 0 auto;line-height: 30rpx;}
</style>

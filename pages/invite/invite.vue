<template>
	<view>
		<view class="">
			<view class="indexBJ"><image src="../../static/images/img.jpg" mode=""></image></view>
			<view class="inviteCont">
				<view class="flexCenter mgb20"><image class="yaoqinghan" src="../../static/images/icon04.png" mode=""></image></view>
				<view class="items fs12 flexColumn">
					<view class="btn flexCenter">
						<view class="w flexRowBetween">
							<view class="ll"><image class="icon" src="../../static/images/icon02.png" mode=""></image></view>
							<view class="rr">
								<view>2020年1月8日 星期三</view>
								<view class="text">Wednesday, Jan 8th, 2020</view>
							</view>
						</view>
					</view>
					<view class="btn flexCenter">
						<view class="w flexRowBetween">
							<view class="ll"><image class="icon" src="../../static/images/icon03.png" mode=""></image></view>
							<view class="rr" style="padding-top: 6rpx;">
								<view>西安万丽酒店 二楼大宴会厅</view>
								<view class="text">The Renaissance Xi'An hotel Grand Ballroom, 2nd Floor</view>
							</view>
						</view>
					</view>
					<view class="btn flexCenter">
						<view class="w flexRowBetween">
							<view class="ll"><image class="icon" src="../../static/images/icon01.png" mode=""></image></view>
							<view class="rr">
								<view>请在16:30前抵达酒店</view>
								<view class="text">Please arrive by 16:30</view>
							</view>
						</view>
					</view>
				</view>
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
	.indexBJ{width: 100%;height: 100%;position: fixed;top: 0;right: 0; bottom: 0;left: 0;z-index: 1;}
	.indexBJ image{width: 100%;height: 100%; display: block;}
	
	.inviteCont{position: fixed;top: 30%;left: 0;right: 0;height:48%;z-index: 10;}
	.yaoqinghan{width: 271rpx;height: 140rpx;display: block;}
	.items{height: 74%;}
	.items .btn{width: 500rpx;padding: 16rpx 30rpx;height: 26%;border-radius:20rpx;border: 1px solid #e30083;line-height: 26rpx;margin-bottom: 3%;box-sizing: border-box;}
	.items .icon{width: 72rpx;height: 72rpx;display: block;}
	.items .rr{width: 77%;}
	.items .rr .text{text-transform:capitalize;margin-top: 6rpx;}
</style>

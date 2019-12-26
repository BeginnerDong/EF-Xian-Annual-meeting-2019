<template>
	<view>
		<view class="indexBJ" style=""></view>
		
		<view class="campusNav fs13 center">
			<view class="item" v-for="(item,index) in campusData" :key="index" @click="Router.navigateTo({route:{path:'/pages/details/details'}})">{{item}}</view>
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
				is_show:false,
				campusData:['Xi′An1小寨校区','Xi′An2高新校区','Xi′An3交大校区','Xi′An4经开校区','Xi′An5曲江校区','Xi′An6高新二校区','Xi′An7咸宁路校区','Xi′An8吉祥路校区','Xi′An9龙首校区','Central&Function']
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
	.indexBJ{width: 100%;height: 100%;background: url(../../static/images/img.jpg) no-repeat 0 0 /100% 100%;position: fixed;top: 0;right: 0; bottom: 0;left: 0;}
	.campusNav{padding:340rpx 18% 0 18%;position:relative;z-index: 2;}
	.campusNav .item{margin-bottom: 8rpx;border: 1px solid #e30083;border-radius: 20rpx;line-height: 60rpx;height: 60rpx;}
	
</style>

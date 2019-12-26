<template>
	<view>
		<view class="">
			<image class="detailPic" src="../../static/images/img1.jpg" mode=""></image>
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
	.detailPic{width: 100%;height: 100%;display: block;position: fixed;top: 0;right: 0;bottom: 0;left: 0;}
	
</style>

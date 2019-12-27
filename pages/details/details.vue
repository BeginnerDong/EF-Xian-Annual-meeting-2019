<template>
	<view>
		<view class="" v-if="is_show">
			<image class="detailPic" 
			:src="mainData.mainImg&&mainData.mainImg.length>0?mainData.mainImg[0].url:'../../static/images/img2.jpg'"  mode="widthFix"></image>
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
				mainData:{}
			}
		},
		
		onLoad(options) {
			const self = this;
			self.name = options.name;
			self.$Utils.loadAll(['getMainData'], self);
		},
		
		
		methods: {
			
			getMainData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id:2
				};
				postData.getBefore = {
					caseData: {
						tableName: 'Label',
						searchItem: {
							title: ['=', [self.name]],
						},
						middleKey: 'menu_id',
						key: 'id',
						condition: 'in',
					},
				};
				const callback = (res) => {
					if (res.solely_code == 100000 && res.info.data[0]) {
						self.mainData = res.info.data[0];
					} 
					self.is_show = true
					self.$Utils.finishFunc('getMainData');
				};
				self.$apis.articleGet(postData, callback);
			},
		}
	};
</script>

<style>
	.detailPic{width: 100%;height: auto;display: block;}
	
</style>

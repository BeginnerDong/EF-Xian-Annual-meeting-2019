<template>
	<view>
		<view class="" v-if="is_show">
			<image  :class="name=='年会信息'||(mainData.mainImg&&mainData.mainImg.length==0)?'detailPicA':'detailPic'"
			:src="mainData.mainImg&&mainData.mainImg.length>0?mainData.mainImg[0].url:'../../static/images/img2.jpg'"  :mode="name=='年会信息'||(mainData.mainImg&&mainData.mainImg.length==0)?'':'widthFix'"></image>
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
				mainData:{},
				name:''
			}
		},
		
		onLoad(options) {
			const self = this;
			
			/* wx.setBackgroundColor({
			    backgroundColor:  '#e30083',
			    backgroundColorBottom: '#e30083'
			}); */
			
			if(options.name){
				self.name = options.name;
			};
			if(options.id){
				self.id = options.id
			};
			self.$Utils.loadAll(['getMainData'], self);
		},
		
		
		methods: {
			
			getMainData() {
				const self = this;
				const postData = {};
				postData.searchItem = {
					thirdapp_id:2
				};
				if(self.name){
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
				};
				if(self.id){
					postData.searchItem.id = self.id
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
	.detailPicA{width: 100%;height: 100%;display: block;position: fixed;top: 0;right: 0;bottom: 0;left: 0;}
</style>

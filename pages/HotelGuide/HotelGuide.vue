<template>
	<view>
		<view class="hotelBox">
			<view class="flexEnd mgt10">
				<image class="login2" src="../../static/images/login2.png" mode="widthFix"></image>
			</view>
			<view class="white pdb10">
				<view class="fs20 ftw">酒店指引</view>
				<view class="pdt5 fs13">Venue Guide</view>
			</view>
			<view class="infor fs12">
				<view class="center">
					<view class="fs13 ftw">EF英孚教育少儿英语西安学校2019年度盛典</view>
					<view class="fs13 ftw pdt5 pdb25">FF Xi'An 2019 Annual Gala Party</view>
					<view>西安万丽酒店 二楼大宴会厅</view>
					<view class="fs11">The Renaissance Xian Hotel Grand Ballroom,2nd Floor</view>
				</view>
				<view class="hotelPic pdtb15">
					<image src="../../static/images/hotel.png" mode="widthFix"></image>
				</view>
				<view class="flex">
					<view class="title">酒店地址：</view>
					<view class="">陕西省西安市曲江新区汇新路355号</view>
				</view>
				<view class="flex mgb20" style="align-items: flex-start;">
					<view class="title">Address:</view>
					<view class="mgl5">No.355 Huixin Road，Qujing New District, Xi'An,ShanXi,China</view>
				</view>
				<view class="mapPic mgb15" @click="toMap()">
					<image :src="mainData.mainImg&&mainData.mainImg[0]?mainData.mainImg[0].url:''" mode=""></image>
				</view>
				<view class="mapPic" @click="toMap()">
					<image :src="mainData.mainImg&&mainData.mainImg[1]?mainData.mainImg[1].url:''" mode=""></image>
				</view>
				<view class="pdt20 chuxingGps">
					<view class="ftw">如何到达</view>
					<view class="item flex">
						<view class="ll">公交出行：</view>
						<view class="rr">曲江国际会展中心站下车步行300米</view>
					</view>
					<view class="item flex">
						<view class="ll">地铁出行：</view>
						<view class="rr">二号线会展中心站C出口，步行1公里或换乘公交至曲江国际会议中心站下车，步行300米</view>
					</view>
					<view class="item flex">
						<view class="ll">自驾出行：</view>
						<view class="rr">导航输入“西安万丽酒店”</view>
					</view>
				</view>
				<view class="pdt20 chuxingGps fs11">
					<view class="ftw">How To Get There：</view>
					<view class="item flex">
						<view class="ll">Bus Line：</view>
						<view class="rr">Qu Jing Guo Ji Hui Zhan Ahogn Xin Stop</view>
					</view>
					<view class="item flex">
						<view class="ll">Subway：</view>
						<view class="rr">Line2,Hui Zhan Zhogn Xin stop, C Exit,then walking 1km</view>
					</view>
					<view class="item flex">
						<view class="ll">Taxi Pin：</view>
						<view class="rr">西安万丽酒店</view>
					</view>
				</view>
			</view>
			
			<view class="white pdt20 center fs12">2019 EF Xi'An Annual Gala Party</view>
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
		
		onLoad() {
			const self = this;
			self.$Utils.loadAll(['getMainData'], self);
		},
		
		methods: {
			
			toMap(){
				const self = this;
				console.log(2332432)
				uni.openLocation({
					latitude: parseFloat(self.mainData.latitude),
					longitude: parseFloat(self.mainData.longitude),
					name:'西安万丽酒店',
					address:'陕西省西安市曲江新区汇新路355号',
					success: function () {
						console.log('success');
					}
				});
			},
			
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
							title: ['=', ['酒店指引']],
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
					self.$Utils.finishFunc('getMainData');
				};
				self.$apis.articleGet(postData, callback);
			},
			
		}
	};
</script>

<style>
	page{background: #e30083;padding-bottom: 80rpx;}
	.hotelBox{margin: 0 6%;}
	.login2{width: 330rpx; display: block;margin-bottom: 80rpx;}
	.hotelBox .infor{background: #fff;border-radius: 60rpx;padding: 50rpx 5%;}
	.hotelPic image{width: 100%;height: auto;border-radius: 30rpx; display: block;}
	.mapPic image{width:594rpx; height: 428rpx; display: block;}
	.chuxingGps .item{align-items: flex-start;}
	.chuxingGps .item .ll{width: 22%;}
	.chuxingGps .item .rr{width: 78%;}
</style>

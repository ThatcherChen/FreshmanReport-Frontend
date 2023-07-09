<template>
	<view>
		<view>
			<u-navbar title-color="#fff" back-icon-color="#ffffff"
				:is-fixed="isFixed" :is-back="isBack" 
				:background="background" 
				:back-text-style="{color: '#fff'}" :title="title1" 
				:back-icon-name="backIconName" :back-text="backText"
				:border-bottom="false" @click="goIndex()">
			</u-navbar>
		</view>
		<u-card :title="title">
			<view class="" slot="body">
				<view class="u-body-item u-flex u-border-bottom u-col-between u-p-t-0">
					<image style="width: 430px; height: 350px; background-color: #eeeeee;" :src="picsrc">
				</view>
			</view>
		</u-card>
		<view class="headLine"> 目的地导航 </view>
		<view class="upView" style="background-image: linear-gradient(90deg, rgb(118, 187, 187), rgb(156, 198, 130));">
		
			<cc-nineMenuBtn class="nineV" @click="yishitang()" myText='一食堂' imgSrc='../../static/images/mappic/shitang1.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="ershitang()" myText='二食堂' imgSrc='../../static/images/mappic/shitang2.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="sanshitang()" myText='三食堂' imgSrc='../../static/images/mappic/shitang3.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="beimeng()" myText='北门' imgSrc='../../static/images/mappic/door1.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="xiyimeng()" myText='西一门' imgSrc='../../static/images/mappic/door2.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="xiermeng()" myText='西二门' imgSrc='../../static/images/mappic/door3.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="kuaididian()" myText='快递点' imgSrc='../../static/images/mappic/kuaidi.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="yijiao()" myText='一教' imgSrc='../../static/images/mappic/building1.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="yishiyan()" myText='一实验楼' imgSrc='../../static/images/mappic/building2.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="zonghelou()" myText='综合楼' imgSrc='../../static/images/mappic/building3.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="yishulou()" myText='艺术楼' imgSrc='../../static/images/mappic/building4.png'></cc-nineMenuBtn>
			<cc-nineMenuBtn class="nineV" @click="tushuguan()" myText='图书馆' imgSrc='../../static/images/mappic/tushuguan.png'></cc-nineMenuBtn>
		
		
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				// 顶部导航栏
				title1: '校园地图',
				backText: '首页',
				backIconName: 'nav-back',
				right: false,
				showAction: false,
				rightSlot: false,
				useSlot: false,
				background: {
					'background-image': 'linear-gradient(90deg, rgb(118, 187, 187), rgb(156, 198, 130))'
				},
				isBack: true,
				search: false,
				custom: true,
				isFixed: true,
				keyword: '',
				// #ifdef MP
				slotRight: false,
				// #endif
				// #ifndef MP
				slotRight: true,
				picsrc:'../../static/images/map.png',
				title: '校园地图：'
			}

		},
		methods: {
			goIndex() {
				console.log("fuck");
				uni.navigateTo({
					url: "pages/index/index"
				});
			},
			//一食堂
			yishitang() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B0FFID3Q2E'
				})
			},
			//二食堂
			ershitang() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B00178XAWM'
				})
			},
			//三食堂
			sanshitang() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B001790TN3'
				})
			},
			//北门
			beimeng() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B0017876J7'
				})
			},
			//西一门
			xiyimeng() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B00178UNDI'
				})
			},
			//西二门
			xiermeng() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B0H25ALSTZ'
				})
			},
			//快递点
			kuaididian() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B0FFJN8V9P'
				})
			},
			//一教
			yijiao() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B00178X6R8'
				})
			},
			//一实验
			yishiyan() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B001790OR9'
				})
			},
			//综合楼
			zonghelou() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B00178X72B'
				})
			},
			//艺术楼
			yishulou() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B00179A28R'
				})
			},
			//图书馆
			tushuguan() {
				uni.navigateTo({
					url: '/pages/frmv/webView?url=' + 'https://www.amap.com/place/B00178X66H'
				})
			},

		}
	}
</script>

<style scoped lang="scss">
	page {
		background-image: linear-gradient(90deg, rgb(118, 187, 187), rgb(156, 198, 130));
	}
	.u-card-wrap {
		background-color: $u-bg-color;
		padding: 20px;
	}

	.u-body-item {
		font-size: 30rpx;
		color: #221233;
		padding: 0rpx 0rpx;
	}

	.u-body-item image {
		height: 821rpx;
		width: 474rpx;
		margin-left: 12rpx;
	}

	.grid-text {
		font-size: 10rpx;
		margin-top: 10rpx;
		margin-left: 5rpx;
		margin-right: 5rpx;
		color: $u-type-info;
	}
	/* .u-grid-item{
		padding: 50rpx 50rpx;
	} */
	.u-grid-item-box{
		padding: 50rpx 50rpx;
	}
	.content {
		display: flex;
		flex-direction: column;
	
	}
	
	.upView {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		margin-left: 12px;
		width: calc(100vw - 24px);
		margin-top: 10px;
		padding: 4px 0px;
		background-color: white;
	
	}
	
	.headLine {
		text-align: center;
		height: 30px;
		line-height: 30px;
		margin: 10px 15px;
		font-size: 20px;
	}
	
	.nineV {
	
		width: calc((100vw - 24px)/3);
	}
</style>
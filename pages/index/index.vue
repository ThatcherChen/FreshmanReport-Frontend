<template>

	<view class="u-wrap">
		<view>
			<u-swiper :list="slideshowlist"></u-swiper>
		</view>
		<view>
			<u-notice-bar mode="horizontal" :list="scrolllist"></u-notice-bar>
		</view>
		<view class="">
			<view class="u-card-wrap">
				<u-card @click="goInform()" :title="titley" :thumb="thumby" :padding="paddingy" :border="bordery"
					:head-border-bottom="hbby" :foot-border-top="fbty">
					<view class="" slot="body">
						<view class="u-body-item u-flex u-border-bottom u-col-between u-p-t-0">
							<view class="u-body-item-title u-line-2">
								请认真查看报道须知
							</view>
						</view>
					</view>
				</u-card>
			</view>
		</view>

		<view class="">
			<view class="u-card-wrap">
				<u-card @click="goFlow()" :title="titlez" :thumb="thumbz" :padding="paddingz" :border="borderz"
					:head-border-bottom="hbbz" :foot-border-top="fbtz">
					<view class="" slot="body">
						<view class="u-body-item u-flex u-border-bottom u-col-between u-p-t-0">
							<view class="u-body-item-title u-line-2">
								请认真查看报道流程
							</view>
						</view>
					</view>
				</u-card>
			</view>
		</view>

		<view class="">
			<view class="u-card-wrap">
				<u-card @click="goCollect()" :title="titlex" :thumb="thumbx" :padding="paddingx" :border="borderx"
					:head-border-bottom="hbbx" :foot-border-top="fbtx">
					<view class="" slot="body">
						<view class="u-body-item u-flex u-border-bottom u-col-between u-p-t-0">
							<view class="u-body-item-title u-line-2">
								请认真核对并填写个人信息
							</view>
						</view>
					</view>
				</u-card>
			</view>
		</view>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				
				scrolllist: [
					'寒雨连江夜入吴',
					'平明送客楚山孤',
					'洛阳亲友如相问',
					'一片冰心在玉壶'
				],
				slideshowlist: [{
						image: '/static/images/slideshowpic/1.jpg',
						title: '迎新大会'
					},
					{
						image: '/static/images/slideshowpic/2.PNG',
						title: '图书馆指南'
					},
					{
						image: '/static/images/slideshowpic/3.PNG',
						title: '校园萌宠'
					}
				],
				titley: '报道须知',
				thumby: '../../static/images/inform.png',
				paddingy: 20,
				bordery: false,
				hbby: false,
				fbty: false,
				titlez: '报道流程',
				thumbz: '../../static/images/flow.png',
				paddingz: 20,
				borderz: false,
				hbbz: false,
				fbtz: false,
				titlex: '信息采集',
				thumbx: '../../static/images/collect.png',
				paddingx: 20,
				borderx: false,
				hbbx: false,
				fbtx: false
			}
		},
		computed: {

		},
		methods: {
		
			imageError() {

			},
			thumbChange(index) {
				this.thumb = index == 0 ? 'http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg' : '';
			},
			paddingChange(index) {
				this.padding = [20, 30, 40][index];
			},
			bottomChange(index) {
				this.bottomSlot = !index;
			},
			borderChange(index) {
				this.border = !index;
			},
			click(index) {
				console.log(index);
			},
			goInform() {
				uni.navigateTo({
					url: '../frmv/inform'
				})
			},
			goCollect() {
				const value = uni.getStorageSync('user')
				if (value) {
					uni.navigateTo({
						url: '../frmv/collect'
					})
				}
			},
			goFlow() {
				uni.navigateTo({
					url: '../frmv/flow'
				})
			}

		}
	}
</script>

<style scoped lang="scss">
	.wrap {
			padding: 40rpx;
		}
	.u-demo {
		padding-top: 0;
	}

	.u-card-wrap {
		background-color: $u-bg-color;
		padding: 1px;
	}

	.u-body-item {
		font-size: 32rpx;
		color: #333;
		padding: 20rpx 10rpx;
	}

	.u-body-item image {
		width: 120rpx;
		flex: 0 0 120rpx;
		height: 120rpx;
		border-radius: 8rpx;
		margin-left: 12rpx;
	}
</style>
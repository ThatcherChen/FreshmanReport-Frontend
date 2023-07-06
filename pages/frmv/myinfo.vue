<template>
	<view>
		<view v-if="logined">
			<u-navbar :is-back="false" title="　" :border-bottom="false">
				<view class="u-flex u-row-right" style="width: 100%;">
					<view class="camera u-flex u-row-center">
						<u-icon name="camera-fill" color="#000000" size="48"></u-icon>
					</view>
				</view>
			</u-navbar>
			<view class="u-flex user-box u-p-l-30 u-p-r-20 u-p-b-30">
				<view class="u-m-r-10" @click="goSelectheadpic()">
					<u-avatar :src="'/static/images/headpic/'+picid+'.PNG'" size="140"></u-avatar>
				</view>
				<view class="u-flex-1">
					<view class="u-font-18 u-p-b-20">{{yonghu.nickname}}</view>
				</view>
				<view class="u-m-l-10 u-p-10">
					<u-icon name="scan" color="#969799" size="28"></u-icon>
				</view>
				<view class="u-m-l-10 u-p-10" @click="editit()">
					<u-icon name="arrow-right" color="#969799" size="28"></u-icon>
				</view>
			</view>

			<view class="u-m-t-20" @click="quit">
				<u-cell-group>
					<u-cell-item icon="setting" title="退出登录"></u-cell-item>
				</u-cell-group>
			</view>
		</view>
		<view v-else>
			<u-navbar :is-back="false" title="　" :border-bottom="false">
				<view class="u-flex u-row-right" style="width: 100%;">
					<view class="camera u-flex u-row-center">
						<u-icon name="camera-fill" color="#000000" size="48"></u-icon>
					</view>
				</view>
			</u-navbar>
			<view class="u-flex user-box u-p-l-30 u-p-r-20 u-p-b-30">
				<view class="u-m-r-10">
					<u-avatar src="../../static/images/personal.png" size="140"></u-avatar>
				</view>
				<view class="u-flex-1">
					<view class="u-font-18 u-p-b-20">匿名用户</view>
					<view class="u-font-14 u-tips-color">请登录</view>
				</view>

			</view>

			<view class="u-m-t-20" @click="goLogin()">
				<u-cell-group>
					<u-cell-item icon="man-add" title="登录"></u-cell-item>
				</u-cell-group>
			</view>
		</view>

	</view>

</template>

<script>
	export default {
		data() {
			return {
				logined: false,
				picid: 0,
				yonghu: {
					nickname: "游客"
				} //初始
			}
		},
		onShow() {
			try { //见  https://uniapp.dcloud.net.cn/api/storage/storage.html#getstoragesync
				const value = uni.getStorageSync('user');
				this.picid=value.headPicture;
				console.log("个人信息页面获取到user的值为：", value)
				console.log("picid值为：",this.picid)
				if (value) {
					//if (!this.logined)
					//从未登录变为登录
					this.yonghu = value
					
					this.logined = true
				} else {
					console.log("未登录成功，yonghu置空")
					this.yonghu = {}
					this.logined = false
				}
			} catch (e) {
				// error
			}
		},
		methods: {
			goLogin() {
				console.log('转入了登陆页面')
				uni.navigateTo({
					url: '/pages/frmv/login'
				})
			},
			goSelectheadpic() {
				uni.navigateTo({
					url: '/pages/frmv/selectheadpic'
				})
			},
			quit() { //增加
				uni.setStorageSync("user", "");
				uni.setStorageSync('form', ""); //清空 存储
				uni.setStorageSync('student',"");
				console.log('退出')
				this.logined = false //登陆状态
			},
			editit() {
				console.log('从主页转入了设置')
				uni.navigateTo({
					url: '/pages/frmv/editmyinfo'
				})
			}

		}

	}
</script>

<style lang="scss">
	page {
		background-color: #ededed;
	}

	.camera {
		width: 54px;
		height: 44px;

		&:active {
			background-color: #ededed;
		}
	}

	.user-box {
		background-color: #fff;
	}
</style>
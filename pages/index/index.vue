<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<u-button type="primary" @click="login"> 登陆</u-button>
		<button type="default" @click="navnavigator">跳转到新页面</button>
		<u-tabbar :value="tabbar5" :placeholder="true" :fixed="true" :safeAreaInsetBottom="true">
			<u-tabbar-item text="首页" icon="home" @click="click1"></u-tabbar-item>
			<u-tabbar-item text="记录" icon="edit-pen" @click="click1"></u-tabbar-item>
			<u-tabbar-item text="放映厅" icon="photo" @click="click1"></u-tabbar-item>
			<u-tabbar-item text="我的" icon="account" @click="click1"></u-tabbar-item>
		</u-tabbar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				tabbar5: 0,
			}
		},
		onLoad() {

		},
		methods: {
			click1(e) {				
				switch (e) {
					case 0:
						uni.redirectTo({
							url: '/pages/index/index'
						});
						break;
					case 1:
						uni.redirectTo({
							url: '/pages/Logs/Add'
						});
						break;
					case 2:
						uni.redirectTo({
							url: '/pages/Logs/Index'
						});
						break;
					case 3:
						uni.redirectTo({
							url: '/pages/Self'
						});
						break;
				}
			},
			navnavigator(item) {
				uni.redirectTo({
					url: '/pages/Login'
				});
			},
			login(param) {
				console.log("登陆")
				uni.login({
					provider: 'weixin',
					success: function(loginRes) {
						console.log(loginRes.authResult);
						// 获取用户信息
						uni.getUserInfo({
							provider: 'weixin',
							success: function(infoRes) {
								console.log('用户昵称为：' + infoRes.userInfo.nickName);
							}
						});
					}
				});
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>

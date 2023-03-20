<template>
	<view class="content">
		<text class="title">{{title}}</text>
		<button type="default" @click="navigator">返回首页</button>
		<u-button type="primary" @click="login"> 登陆</u-button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '登陆测试'
			}
		},
		onLoad() {

		},
		methods: {
			navigator(item) {				
				uni.redirectTo({
					url: '/pages/index/index'
				});
			},login(param){
				console.log("登陆")
				uni.login({
				  provider: 'weixin',
				  success: function (loginRes) {
				    console.log(loginRes.authResult);
				    // 获取用户信息
				    uni.getUserInfo({
				      provider: 'weixin',
				      success: function (infoRes) {
				        console.log('用户昵称为：' + infoRes.userInfo.nickName);
				      }
				    });
				  }
				});
			}
		}
	}
</script>





<style lang="scss">
	.font10 {
		font-size: 11px;
	}

	.fontcolor1 {
		color: #79879a;
	}
</style>

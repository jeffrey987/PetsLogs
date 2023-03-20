<template>
	<view>
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
				tabbar5: 3,
			}
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
		}
	}
</script>

<style>

</style>

<template>
	<view class="bg_color">
		<!-- 注意，如果需要兼容微信小程序，最好通过setRules方法设置rules规则 -->
		<u--form labelPosition="left" :model="model1" :rules="rules" ref="form1" class="add-form">
			<u-form-item>
				<view class="item-text">记录宠物:</view>
				<u--input v-model="model1.petInfo.name" border="none"></u--input>
			</u-form-item>
			<u-form-item label="" prop="">
				<view class="item-text">大事类型:</view>
				<u--input v-model="model1.petInfo.type" border="none"></u--input>
			</u-form-item>
			<u-form-item label="" prop="">
				<view class="item-text">记录时间:</view>
				<view  @click="show = true" >{{model1.petInfo.reminderdate}}</view>
				<u-calendar :show="show" :mode="mode" @confirm="confirm"></u-calendar>				
				<!-- 时间选择 -->
			</u-form-item>
			<u-form-item label="描述:">
				<u-textarea v-model="model1.petInfo.content" placeholder="如果你把我拍的很可爱，我可以允许你把他记下来"></u-textarea>
			</u-form-item>
			<u-form-item>
				<u-checkbox-group>
					<u-checkbox v-model="model1.petInfo.hasindex" />是否在首页显示
				</u-checkbox-group>
			</u-form-item>
		</u--form>
		<view class="add-form-button">
			<u-button type="primary" shape="circle" @click="submit">提交</u-button>
		</view>
		<u-action-sheet :show="showSex" :actions="actions" title="请选择性别" description="如果选择保密会报错"
			@close="showSex = false" @select="sexSelect">
		</u-action-sheet>

		<u-tabbar :value="tabbar5" :placeholder="true" :fixed="true" :safeAreaInsetBottom="true">
			<u-tabbar-item text="首页" icon="home" dot @click="click1"></u-tabbar-item>
			<u-tabbar-item text="记录" icon="edit-pen" @click="click1"></u-tabbar-item>
			<u-tabbar-item text="放映厅" icon="photo" badge="3" @click="click1"></u-tabbar-item>
			<u-tabbar-item text="我的" icon="account" @click="click1"></u-tabbar-item>
		</u-tabbar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabbar5: 1,
				showSex: false,
				show: false,
				mode: 'single',
				model1: {
					userInfo: {
						name: 'uView UI',
						sex: '',
					},
					petInfo: {
						name: 'name',
						title: '提醒名称',
						type: '提醒类型',
						reminderdate: '2023-1-1',
						remindertype: 1,
						remindertime: '16:00',
						hasindex: true,
					}
				},
				actions: [{
						name: '男',
					},
					{
						name: '女',
					},
					{
						name: '保密',
					},
				],
				rules: {
					'userInfo.name': {
						type: 'string',
						required: true,
						message: '请填写姓名',
						trigger: ['blur', 'change']
					},
					'userInfo.sex': {
						type: 'string',
						max: 1,
						required: true,
						message: '请选择男或女',
						trigger: ['blur', 'change']
					},
				},
				radio: '',
				switchVal: false
			};
		},
		methods: {
			confirm(e) {
				this.show=false;
				console.log(e[0]);
				this.model1.petInfo.reminderdate=e[0]
			},
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
			sexSelect(e) {
				this.model1.userInfo.sex = e.name
				this.$refs.form1.validateField('userInfo.sex')
			},
		},
		onReady() {
			//如果需要兼容微信小程序，并且校验规则中含有方法等，只能通过setRules方法设置规则。
			this.$refs.form1.setRules(this.rules)
		}
	}
</script>

<style lang="scss">
	.bg_color {
		background-color: #F3F2EB;
		padding: 20px 0;
		margin: 0;

		.add-form {
			margin: 0px 15px;
			padding: 0px 10px;
			border-radius: 15px;
			background-color: #FEFEFE;
		}

		.item-text {
			font-weight: bold;
			padding-right: 5px;
			font-size: 15px;
		}

		.add-form-button {
			margin: 20px 15px 0px 15px;
		}
	}
</style>
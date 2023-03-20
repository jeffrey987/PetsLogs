<template>
	<view>
		<!-- 注意，如果需要兼容微信小程序，最好通过setRules方法设置rules规则 -->
		<u--form labelPosition="left" :model="model1" :rules="rules" ref="form1">
			<u-form-item label="记录宠物"  borderBottom >
				<u--input v-model="model1.petInfo.name" border="none"></u--input>
			</u-form-item>
			<u-form-item label="提醒名称" prop="userInfo.name" borderBottom >
				<u--input v-model="model1.petInfo.title" border="none"></u--input>
			</u-form-item>
			<u-form-item label="提醒类型" prop="userInfo.name" borderBottom >
				<u--input v-model="model1.petInfo.title" border="none"></u--input>
			</u-form-item>
			<u-form-item label="计划日期" prop="userInfo.name" borderBottom >
				<u--input v-model="model1.petInfo.title" border="none"></u--input>
			</u-form-item>
			<u-form-item label="计 划周期" prop="userInfo.name" borderBottom >
				<u--input v-model="model1.petInfo.title" border="none"></u--input>
			</u-form-item>
			<u-form-item label="提醒时间" prop="userInfo.name" borderBottom >
				<u--input v-model="model1.petInfo.title" border="none"></u--input>
			</u-form-item>
			
		</u--form>
		<u-button type="primary" shape="circle" @click="submit">提交</u-button>
		<u-action-sheet :show="showSex" :actions="actions" title="请选择性别" description="如果选择保密会报错"
			@close="showSex = false" @select="sexSelect">
		</u-action-sheet>

		<u-tabbar :value="tabbar5" :placeholder="true" :fixed="true" :safeAreaInsetBottom="true">
			<u-tabbar-item text="首页" icon="home" dot></u-tabbar-item>
			<u-tabbar-item text="放映厅" icon="photo" badge="3"></u-tabbar-item>
			<u-tabbar-item text="我的" icon="account"></u-tabbar-item>
		</u-tabbar>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabbar5: 0,
				showSex: false,
				model1: {
					userInfo: {
						name: 'uView UI',
						sex: '',
					},
					petInfo:{
						name:'name',
						title:'提醒名称',
						type:'提醒类型',
						reminderdate:'2023-1-1',
						remindertype:1,
						remindertime:'16:00',
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
			sexSelect(e) {
				this.model1.userInfo.sex = e.name
				this.$refs.form1.validateField('userInfo.sex')
			},
		},
		onReady() {
			//如果需要兼容微信小程序，并且校验规则中含有方法等，只能通过setRules方法设置规则。
			this.$refs.form1.setRules(this.rules)
		},
	}
</script>

<style lang="scss">

</style>

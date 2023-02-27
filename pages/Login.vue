<template>
	<view>
		<u-tabs :list="list1" @click="click"></u-tabs>
		<view class="u-page">
			<view class="u-demo-block">
				<u-tabs :list="list2" @click="click2"></u-tabs>
				<view class="u-demo-block__content" style="margin-top:15px;" >
					<u-row customStyle="margin-bottom: 10px">
						<u-col span="4">
							<u--image src="https://cdn.uviewui.com/uview/album/1.jpg" width="80px" height="80px"
								shape="circle"></u--image>
						</u-col>
						<u-col span="8">
							<u-row>
								<u-col span="6">
									<view class=""><strong>123</strong> </view>
								</u-col>
							</u-row>
							<u-row class="font10 fontcolor1">
								<u-col span="4">
									<view class=" ">中华田园犬</view>
								</u-col>
								<u-col span="4">
									<view class=" ">补充年龄</view>
								</u-col>
								<u-col span="4">
									<view class=" ">补充体重</view>
								</u-col>
							</u-row>
						</u-col>
					</u-row>
					<u-row class="div-daojia">
						<u-col>
							<view style="background-color: #F6F2DE;	padding: 10px 0px 10px 10px;border-radius: 10px;">
								补充宠物到家日期</view>
						</u-col>
					</u-row>
				</view>
			</view>
		</view>
		<!-- 重要事项提醒 -->
		<view class="quick-settings">
			<u-row>
				<u-col span="2"><u--image src="https://cdn.uviewui.com/uview/album/1.jpg" width="50px" height="50px"></u--image> </u-col>
				<u-col span="6">
					<view class="nlock_text">重要事项提醒</view>
					<view class="nlock_text">重要事项提醒</view>
				</u-col>
				<u-col span="4">
					<u-button type="primary" text="去设置"></u-button>
				</u-col>
			</u-row>
		</view>
		<!-- 记录列表  start-->
		<view>
			<u-list>
				<u-list-item v-for="(item, index) in indexList" :key="index">
					<template>
						<view class="list-block-content">
							<view class="petinfo">
								{{item.date}}
							</view>
							<view class="album">
								<view class="album__title">{{item.title}}</view>
								<view class="album__content">									
									<u--text class="album_content_text" :text="item.content"></u--text>
									<u-album :urls="item.imgs"></u-album>
								</view>
							</view>
						</view>
					</template>
				</u-list-item>
			</u-list>
		</view>
		<!-- 记录列表  end-->

	</view>
</template>

<script>
	export default {
		data() {
			return {
				indexList: [{
					date: "2023-02-14 15:18",
					title: "title1",
					pet: "pet",
					content: "content",
					imgs: [
						'https://cdn.uviewui.com/uview/album/1.jpg',
						'https://cdn.uviewui.com/uview/album/2.jpg',
						'https://cdn.uviewui.com/uview/album/3.jpg',
						'https://cdn.uviewui.com/uview/album/4.jpg',
						'https://cdn.uviewui.com/uview/album/5.jpg',
						'https://cdn.uviewui.com/uview/album/6.jpg',
						'https://cdn.uviewui.com/uview/album/7.jpg',
						'https://cdn.uviewui.com/uview/album/8.jpg',
						'https://cdn.uviewui.com/uview/album/9.jpg',
						'https://cdn.uviewui.com/uview/album/10.jpg',
					],
					video: "video",
					types: "type",
				}, {
					date: "2023-02-14 15:18",
					name: "name2",
					pet: "pet",
					content: "content",
					imgs: [
						'https://cdn.uviewui.com/uview/album/8.jpg',
						'https://cdn.uviewui.com/uview/album/9.jpg',
						'https://cdn.uviewui.com/uview/album/10.jpg',
					],
					video: "video",
					types: "type",
				}, {
					date: "2023-02-14 15:18",
					name: "name3",
					pet: "pet",
					content: "content",
					imgs: [
						'https://cdn.uviewui.com/uview/album/5.jpg',
						'https://cdn.uviewui.com/uview/album/6.jpg',
						'https://cdn.uviewui.com/uview/album/7.jpg',
					],
					video: "video",
					types: "type",
				}],
				list1: [{
					name: '记录',
				}, {
					name: '关注',
				}],
				list2: [{
					name: '123',
				}, {
					name: '456',
				}],
			}
		},
		methods: {
			click(item) {
				console.log('item', item);
			},
			click2(item) {
				console.log('item', item);
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

	.wrap {
		padding: 12px;
	}

	.demo-layout {
		height: 25px;
		border-radius: 4px;
	}

	.bg-purple {
		background: #CED7E1;
	}

	.bg-purple-light {
		background: #e5e9f2;
	}

	.bg-purple-dark {
		background: #99a9bf;
	}

	.div-daojia {
		margin: 10px 10px 10px 10px;

	}

	.u-page {
		background-color: #F2EFE7;
		margin-top: 20px;
		margin-left: 15px;
		margin-right: 15px;
		border-radius: 10px;
		padding: 15px;
	}

	.petlogs__title {}
	.list-block-content{
		background-color: #ccffcc;
		margin: 15px;
		padding: 10px;
		border-radius: 10px;
	}
	.list-block-content .petinfo{
		font-size: 11px;
		color: #bfbfbf;
	}
	.album{
	.album__title{
		color: #17191c;
		font-size: 15px;
		font-weight: bold;
		margin-top: 9px;
		margin-bottom: 5px;
	}
	.album__content{
		.album_content_text{
			margin-bottom: 10px !important;
			}
		}
	}
	.quick-settings{
		margin:15px;
	}
</style>

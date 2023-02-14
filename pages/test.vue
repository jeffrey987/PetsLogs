<template>
	<view class="u-page">
		<u-list @scrolltolower="scrolltolower">
			<u-list-item v-for="(item, index) in indexList" :key="index">
				<template>
					<view class="u-demo-block__content">
						<view class="album">
							<view class="album__avatar">
								<image src="https://v2.h5.uviewui.com/static/uview/common/logo.png" mode=""
									style="width: 32px;height: 32px;"></image>
							</view>
							<view class="album__content">
								<u--text text="uView UI" type="primary" bold size="17"></u--text>
								<u--text margin="0 0 8px 0" text="全面的组件和便捷的工具会让您信手拈来，如鱼得水"></u--text>
								<u-album :urls="urls"></u-album>
							</view>
						</view>
					</view>
				</template>
			</u-list-item>
		</u-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				indexList: [],
				urls: [
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
				]
			}
		},
		onLoad() {
			this.loadmore()
		},
		methods: {
			scrolltolower() {
				this.loadmore()
			},
			loadmore() {
				for (let i = 0; i < 30; i++) {
					this.indexList.push({
						url: this.urls[uni.$u.random(0, this.urls.length - 1)]
					})
				}
			}
		},
	}
</script>

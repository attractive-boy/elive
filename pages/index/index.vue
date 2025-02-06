<template>
	<view class="content">

		<view class="banner-container">
			<u-image src="/static/banner.jpg" mode="aspectFit" width="1000rpx" height="400rpx"></u-image>
		</view>
		<view class="content-container">
			<view class="content-user-login" @click="tome">
				<u-avatar :src="avatar_url" shape="circle" size="30"></u-avatar>
				<view style="width: 30rpx;"></view>
				<u-text :text="user_nick_name"></u-text>
			</view>
			<view class="content-user-control">
				<view style="width: 60vw;">
					<u-tabs :list="live_type" @click="change_live_type" :itemStyle="{ padding: '15rpx' }"></u-tabs>
				</view>
				<u-search placeholder="搜一下" v-model="keyword" :showAction="false"></u-search>
			</view>


		</view>
	</view>

</template>

<script>
export default {
	data() {
		return {
			avatar_url: '',
			user_nick_name: '立即登录',
			live_type: [
				{
					name: '最近',
					value: 0
				},
				{
					name: '直播中',
					value: 1
				},
				{
					name: '未开始',
					value: 2
				},
				{
					name: '已结束',
					value: 3
				}
			],
			current_live_type: 0,
			keyword: ''

		}
	},
	onLoad() {

	},
	methods: {
		change_live_type(val) {
			this.current_live_type = val;
		},
		tome() {
			uni.navigateTo({
				url: '/pages/me/me'
			})
		}
	}
}
</script>

<style>
.banner-container {
	display: flex;
	justify-content: center;
	align-items: flex-start;
	width: 100%;
	height: 400rpx;
	background: linear-gradient(180deg, #0d90fe, #2b4dff 35%, #2b4dff);
	transform: translateY(-100rpx);
}

.content-container {
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
	align-items: flex-start;
	width: 100%;
	height: calc(100vh - 300rpx);
	transform: translateY(-200rpx);
	background-color: white;
	border-radius: 30rpx;
}

.content-user-login {
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	/* 间隔: 20rpx; */
	align-items: center;
	width: 100%;
	height: 100rpx;
	padding: 30rpx;
	box-sizing: border-box;
}

.content-user-control {
	display: flex;
	flex-direction: row;
	justify-content: flex-start;
	align-items: center;
	height: 100rpx;
	padding: 30rpx;
	box-sizing: border-box;
}
</style>
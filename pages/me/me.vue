<template>
	<view>
		<view
			style="width: 100%; height: 40vh; background-image: url('/static/me.png'); background-size: cover; background-position: center; background-repeat: no-repeat;">
		</view>
		<view style="transform: translateY(-400rpx);">
			<view style="display: flex; flex-direction: row;" @click="loginshow = true">
				<view style="width: 30rpx;"></view>
				<u-avatar :size="50" :src="user_avatar" style="margin: 0 30rpx"></u-avatar>
				<view style="width: 30rpx;"></view>
				<u-text :text="user_name" size="15"></u-text>

			</view>
			<view
				style="background-color: white;border-radius: 20rpx;width: calc(100% - 60rpx); margin-left: 30rpx; margin-top: 30rpx; box-shadow: 0 0 10rpx rgba(0, 0, 0, 0.1);">
				<view style="padding:0 20rpx;">
					<u-cell-group>
						<u-cell title="文件盘" value="0.00G/100G" :isLink="true"></u-cell>
						<u-cell title="我的订单" :is-link="true"></u-cell>
						<u-cell title="自动预约" :is-link="true" value="未开启"></u-cell>
						<u-cell title="数据报告" :is-link="true"></u-cell>
						<u-cell title="手机号" :is-link="true"></u-cell>
						<u-cell title="实名认证" :is-link="true" value="未认证,请先绑定手机号"></u-cell>
						<u-cell title="账号注销" :is-link="true" value=""></u-cell>
						<u-cell title="协议和说明" :is-link="true" value=""></u-cell>
						<u-cell title="鹅直播APP" :is-link="true" value=""></u-cell>
					</u-cell-group>
				</view>
			</view>
		</view>
		<u-popup :show="loginshow" @close="closelogin" @open="openlogin">
			<view style="margin: 30rpx;">
				<u-text text="获取用户信息"></u-text>
				<u-text text="点击头像或昵称可进行修改" style="color: gray;" size="10"></u-text>
				<view style="display: flex; flex-direction: column; margin-top: 30rpx; align-items: center; width: 100%;">
					<button open-type="chooseAvatar" @chooseavatar="bindchooseavatar" style="margin-bottom: 20rpx; border: none; background: none; box-shadow: none; padding: 0; border-radius: 50%;">
						<u-avatar :size="50" :src="login_user.user_avatar"   ></u-avatar>
					</button>
					<view style="display: flex; flex-direction: row; margin-bottom: 20rpx;">
						<u-text text="昵称"></u-text>
						<u-input v-model="login_user.user_name" placeholder="请输入昵称"></u-input>
					</view>
				</view>
				<u-button type="primary" @click="login">确定</u-button>
			</view>
		</u-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				user_avatar: '',
				user_name: '未登录',
				loginshow: false,
				login_user: {
					user_name: '',
					user_avatar: '',
				}

			}
		},
		onLoad() {
			this.user_avatar = uni.getStorageSync('user_avatar')
			this.user_name = uni.getStorageSync('user_name') || '未登录'
		},
		methods: {
			closelogin() {
				this.loginshow = false
			},
			openlogin() {
				this.loginshow = true
			},
			bindchooseavatar(event){
				this.login_user.user_avatar = event.detail.avatarUrl
			}
		}
	}
</script>

<style></style>
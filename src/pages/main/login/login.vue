<template>
	<view class="login">
		<view class="login-title">
		<p class="univisityname">电子科技大学</p>
		<p class="systemname">请销假</p>
		</view>
		<view class="login-content">
			<p class="welcome">Hi,欢迎登录请销假</p>
			<input type="text" class="uni-input" focus placeholder="学号">
			<button type="primary" class="login-btn" @click="login">登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'login',
		methods:{
			login () {
				// switchTab跳转到tabs的页面
				// navigateTo跳转到非tabs页面
				uni.switchTab({
					url: '/pages/main/home/home'
				})
			}
		}
	}
</script>

<style scoped lang="less">
	.login{
		height: 100%;
		background: #fff;
		/* background: #007AFF; */
	.login-title{
		padding: 20% 10%;
	}
	.systemname{
		font-size: 2rem;
		font-weight: bold;
		}
	.univisityname{
		font-size: 2rem;
	}
		.login-content{
		padding: 0 10%;
		}
		.welcome{
			color: #2C2CA0;
		}
		.uni-input{
			border: 1px solid #2C2CA0;
			border-radius: 3rem;
			margin: 2.5rem 0;
		}
		.login-btn{
			background: #252577;
			border-radius: 3rem;
		}
	}
</style>

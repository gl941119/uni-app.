<template>
	<view class="stay-school-box">
		<form>
			<view class="form-item">
				<view class="title">本人联系电话</view>
                <input class="uni-input" focus placeholder="本人联系电话" />
			</view>
			<view class="form-item">
				<view class="title">家庭联系电话</view>
                <input class="uni-input" focus placeholder="家庭联系电话" />
			</view>
		</form>
		<view class="footer-box">
			<button type="primary" size="small" class="login-btn" @click="submit">提交</button>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'stay-school-register',
		methods: {
			async submit () {	
			await uni.showToast({
				title: '登记成功',
				icon: {
					none: true
				},
				duration: 2000
			})
			uni.switchTab({url: '/pages/main/home/home'})
			}
		}
	}
</script>

<style scoped lang="less">
	.stay-school-box{
		padding: 1rem 0;
	.form-item{
		padding: 0 1rem;
		background: #fff;
		border-bottom: 1px solid #E3E3E3;
			display: flex;
			align-items: center;
		.title{
			width: 4.5rem;
		}
		input{
			padding-left: 1rem;
			
		}
	}
	.footer-box{
		position: fixed;
		width: 100%;
		background: #fff;
		bottom: 0;
		padding: .8rem 0;
	}
		.login-btn{
			width: 80%;
			background: #252577;
			border-radius: 3rem;
		}
	}
</style>

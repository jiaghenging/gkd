<template>
	<view class="content">
		<view class="status_bar">
			<!-- 这里是状态栏 -->
		</view>
		<view class="fixed-bg">
			<video id="homevideo" object-fit="cover" autoplay="autoplay" loop="loop" muted="muted"
				src="../../static/img/bg_login.mp4" :controls="false" class="fixed-video"></video>
		</view>
		<view class="login_container">
			<view class="formBox">
				<text class="login_title">Hi , 你好啊</text>
				<uni-forms ref="form" :model="userForm" :rules="rules" class="login_form">
					<uni-forms-item label="" name="userId">
						<view class="inputBox">
							<input type="text" placeholder="请输入用户名" v-model="userForm.userId"
								placeholder-class="input_style">
						</view>
					</uni-forms-item>
					<uni-forms-item label="" name="userPwd">
						<view class="inputBox">
							<input type="text" placeholder="请输入密码" v-model="userForm.userPwd" password="true"
								placeholder-class="input_style">
						</view>
					</uni-forms-item>
					<uni-forms-item label="" name="ifAgree">
						<view class="form_agrement">
							<view class="checked_box" @tap="ifAgree=!ifAgree">
								<view class="agre_circle" v-show="ifAgree==false"></view>
								<view class="agre_circle2" v-show="ifAgree==true">
									<text class="iconfont icon-check"></text>
								</view>
							</view>
							<text class="agre_txt">
								我已阅读并同意
								<text class="agreement_info" @tap="toAgreement(1)">用户协议</text>
								及
								<text class="agreement_info" @tap="toAgreement(2)">隐私政策</text>
							</text>
						</view>
					</uni-forms-item>
					<uni-forms-item label="" name="">
						<view class="login_btn" @tap="checkForm()">登录/注册</view>
					</uni-forms-item>
				</uni-forms>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				rules: {
					// 对name字段进行必填验证
					userId: {
						rules: [{
								required: true,
								errorMessage: '请输入姓名',
							},
							{
								minLength: 3,
								maxLength: 15,
								errorMessage: '姓名长度在 {minLength} 到 {maxLength} 个字符',
							}
						]
					},
					// 对email字段进行必填验证
					userPwd: {
						rules: [{
								required: true,
								errorMessage: '请输入密码',
							},
							{
								minLength: 6,
								maxLength: 14,
								errorMessage: '密码长度在 {minLength} 到 {maxLength} 个字符',
							}
						]
					}
				},
				ifAgree: false,
				userForm: {
					userId: '',
					userPwd: ''
				}
			}
		},
		methods: {
			checkForm() {
				const that = this;
				
				if (that.ifAgree) {
					that.$refs.form.validate().then(res => {
						console.log('成功：', res);
						uni.switchTab({
						    url: '../index/index'
						});
					}).catch(err => {
						console.log('失败：', err);
					})
				} else {
					uni.showToast({
						title: '请勾选同意后再进行登录奥~',
						duration: 1500,
						icon: 'none'
					})
				}
			}
		}
	}
</script>

<style>
	@import url('../../static/css/login/login.css');
</style>

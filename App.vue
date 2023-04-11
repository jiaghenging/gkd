<script>
	export default {
		globalData: {
		    // baseUrl:'http://192.168.2.68:2300/',
			baseUrl:'http://218.6.173.71:2312/',
			userMsg:{
				userid:'',
				username:''
			}
		},
		onLaunch: function() {
			console.warn('当前组件仅支持 uni_modules 目录结构 ，请升级 HBuilderX 到 3.1.0 版本以上！')
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style lang="scss">
	@import 'static/css/public/iconfont.css';
	@import 'static/css/public/public.css';
	/*每个页面公共css */
	uni-page-body,page {
		height:100%
	}
</style>

<template>
	<div class="container">
		<div class="main">
			<div class="header">
				<img :src="userinfo.avatarUrl" alt="">
				<p>{{userinfo.nickName}}</p>
			</div>
			<div class="body">
				<button>添加地址</button>
				<div class="order">
					<p>我的订单</p>
				</div>
			</div>
		</div>
		<button v-if="!userinfo.nickName" class="btn" open-type="getUserInfo" @click="getUserInfo">登陆</button>		
	</div>
</template>

<script>
import qcloud from 'wafer2-client-sdk'
import config from '../../config.js'
import {showSuccess} from '../../utli.js'
export default {
	data () {
		return {
			userinfo:{
				nickName: '',
				avatarUrl: ''
			}
		}
	},
	methods: {
		getUserInfo() {
			const self = this
			qcloud.setLoginUrl(config.loginUrl)
			qcloud.login({
				success (userinfo) {
					showSuccess('登陆成功')
					wx.setStorageSync('userinfo',userinfo)
					self.userinfo = userinfo
				},
				fail (err) { 
					console.log('登陆失败', err)
				} 
			})
		}
	},
	onShow () {
		let userinfo = wx.getStorageSync('userinfo')
		if (userinfo) {
			this.userinfo = userinfo
		}
	}
}
</script>

<style lang="stylus">
.btn
	width 420rpx
	position absolute
	top 50%
	left 50%
	transform translate(-50%,-50%)
.main
	position absolute
	background #f4f2e6
	top 0
	left 0
	right 0
	bottom 0
	.header
		width 100%
		height 200rpx
		background #ede19e
		overflow hidden
		img
			width 150rpx
			height 150rpx
			border-radius 50%
			float left
			margin-top 25rpx
			margin-left 25rpx
			margin-right 30rpx
		p
			line-height 200rpx
			font-size 20px
	.body
		margin-top 20rpx
		button 
			width 90%
		.order
			margin 0 auto
			margin-top 20rpx
			p
				padding-top 20rpx
				text-align center
</style>


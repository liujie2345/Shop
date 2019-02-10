<template>
	<div class="main">
		<ul class="title" id="a">
			<li 
			v-for="item of title" 
			:key="item.id"
			@click="changeCss(item)"
			:class="{changeColor:item.isActive}"
			ref="a"
			>{{item.name}}</li>
		</ul>
		<button @click="getClassInfo">clicj</button>
	</div>
</template>

<script>
import axios from 'axios'
export default {
	name: 'classLeft',
	data () {
		return {
			title:[
				{
					name: '女装',
					isActive: false
				},
				{
					name: '男装',
					isActive: false
				},
				{
					name: '男女内衣',
					isActive: false
				},
				{
					name: '女鞋',
					isActive: false
				},
				{
					name: '男鞋',
					isActive: false
				},
			]
		}
	},
	methods: {
		changeCss (item) {
			this.title.forEach(v => {
				v.isActive = false
			});
			item.isActive = true
		},
		getClassInfo () {
			axios.get('../../../static/mocks/class.json').then(this.getClassInfoSucc)
		},
		getClassInfoSucc (res) {
			console.log(res)
		}
	},
	onLoad () {
		console.log('11111')
		this.getClassInfo()
	}
}
</script>

<style lang="stylus" scoped>
.main
	.title
		width 100%      
		li
			line-height 100rpx
			font-size 16px
			width 80%
			text-align center
			margin 0 auto
			border-bottom 1rpx solid #edeaea
		.changeColor
			color #ede19e
</style>


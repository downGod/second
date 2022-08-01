<template>
	<view class="container">
		<view class="header" :style="{width:head.w+'px',height:head.h+'px',marginTop:head.top+'px'}">
			<image src="https://class.m.imooc.com/static/wap/static/common/img/logo2.png" mode=""></image>
			<uni-icons type="search" size="24"></uni-icons><strong></strong>
		</view>
		<view class="nav1">
			<text>首页</text>
			<text>免费课</text>
			<text>实战课</text>
			<text class="active">体系课</text>	
		</view>
		<view class="nav2">
			<text>专栏</text>
			<text>手记</text>
			<text>慕课教程</text>
		</view>
		<view class="body">
			<view class="top">
				<text>全部</text>
				<text>零基础</text>
				<text>进阶课</text>
			</view>
		</view>
	</view>
</template>

<script>
	import request from "@/api/index.js"
	export default {
		data() {
			return {
				head:{
					w:"",
					h:"",
					top:""
				}
			}
		},
		methods: {
			fn(){
				const cont = uni.getMenuButtonBoundingClientRect()
				const client = uni.getSystemInfoSync()
				this.head.w = client.windowWidth-(client.windowWidth-cont.right)-client.width
				this.head.h = cont.height
				this.head.top = cont.top
			},
			async getNav1(){
				let {data} = await request({url:"/ai/nav1"})
				console.log(data)
			}
		},
		created(){
			this.fn()
			// this.getNav1()
		}
	}
</script>

<style lang="scss">
	.container {
		.header{
			display: flex;
			justify-content: space-between;
			align-items: center;
			box-sizing: border-box;
			padding: 0 10px;
			image{
				width: 82px;
				height: 24px;
			}
		}
		.nav1,.nav2{
			font-size:16px;
			line-height: 26px;
			margin-top:14px;
			padding: 0 22px;
			box-sizing: border-box;
			font-weight: 700;
			text{
				color:#71777D;
				margin-right: 24px;
			}
			.active{
					color: #f00000;
			}
			
		}
		.body{
			background-color: #EFF1F3;
			width: 100%;
			height: 300px;
			overflow: auto;
			box-sizing: border-box;
			padding:0 10px;
			.top{
				display: flex;
				height: 46px;
				align-items: center;
				font-size: 16px;
				text{
					margin-right:15px
				}
			}
		}
	}
</style>

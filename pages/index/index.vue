<template>
	<view class="content">
		首页
	</view>
</template>

<script>
	export default {
		data() {
			return {
				menu: ['课程专业','排序方式','条件筛选'],
				allCouList: [{
					courseName:'8月22号小周末线上学习'
				},{
					courseName:'8月22号小周末线上学习'
				},{
					courseName:'8月22号小周末线上学习'
				},{
					courseName:'8月22号小周末线上学习'
				},{
					courseName:'8月22号小周末线上学习'
				},]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.course{
		display: flex;
	}
	
	.course>li{
		width: 33.33%;
		flex: 1;
		text-align: center;
		font-size: 0.82rem;
		color: #333;
		line-height: 90rpx;
		border-bottom: 1rpx solid #eee;
		position: relative;
		z-index: 2;
		background: #fff;
	}
	
	.course>li:after {
    content: '';
    display: inline-block;
    vertical-align: 4rpx;
    width: 0;
    height: 0;
    border-left: 6rpx solid transparent;
    border-right: 6rpx solid transparent;
    border-top: 6rpx solid #bbb;
    margin-left: 4rpx;
	}
	
	.course-item-wrap{
		display: flex;
	}
	
	.course-ul>li{
		border-bottom: 1px solid #E9E9E9;
		padding: 10rpx 0;
		position: relative;
	}
	
	.course-img{
		width: 253rpx;
		height: 141rpx;
		margin: 0 20rpx;
		overflow: hidden;
	}
	
	.course-img>image{
		width: 100%;
		height: 100%;
	}
	
	.course-title{
		font-size: 32rpx;
	}
</style>

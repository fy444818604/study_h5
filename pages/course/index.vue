<template>
	<view class="content">
		<ul class="course" @ontouch="showDiloag">
			<li v-for="item in menu">{{item}}</li>
		</ul>
		<ul class="filter-wrap">
			<li>
				<ul class="subject-wrap">
					<li v-for="item in courseList">{{item.subjectName}}</li>
				</ul>
			</li>
		</ul>
		<ul class="course-ul">
			<li v-for="item in allCouList">
				<navigator>
					<div class="course-item-wrap">
						<div class="course-img">
							<image src="../../static/logo.png" mode="widthFix"></image>
						</div>
						<div>
							<div class="course-title">{{item.courseName}}</div>
						</div>
					</div>
				</navigator>
			</li>
		</ul>
		<uni-popup ref="popup" type="bottom">底部弹出 Popup</uni-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				menu: ['课程专业','排序方式','条件筛选'],
				courseList:[{
					subjectId: 0,
					subjectName:'全部'
				},{
					subjectId: 1,
					subjectName:'小学'
				},{
					subjectId: 2,
					subjectName:'初中'
				},{
					subjectId: 3,
					subjectName:'高中'
				},{
					subjectId: 4,
					subjectName:'职高'
				},{
					subjectId: 5,
					subjectName:'学前'
				},{
					subjectId: 4,
					subjectName:'职高'
				},{
					subjectId: 5,
					subjectName:'学前'
				}],
				sortList: [],
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
		mounted() {
			this.$refs.popup.open()
		},
		methods: {
			showDiloag() {
				console.log(123)
				this.$refs.popup.open()
			}
		}
	}
</script>

<style>
	.course{
		display: flex;
		position: relative;
		z-index: 998;
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
	
	.filter-wrap{
		position: absolute;
		display: flex;
		background: #eee;
		overflow: auto;
		width: 100%;
		max-height: 550rpx;
		z-index: 998;
	}
	.filter-wrap>li{
		width: 100%;
	}
	
	.subject-wrap>li {
		height: 90rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	
</style>

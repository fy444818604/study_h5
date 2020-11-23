<template>
	<view class="content">
		<ul class="course">
			<li v-for="(item,index) in menu" @tap="showDiloag(index)">{{item}}</li>
		</ul>
		<ul class="filter-wrap">
			<li v-show="searchNum == 1">
				<ul class="subject-wrap">
					<li v-for="item in courseList" :class="item.active?'active':''">{{item.subjectName}}</li>
				</ul>
			</li>
			<li v-show="searchNum == 2">
				<ul class="subject-wrap">
					<li v-for="item in orderShow" :class="item.active?'active':''">{{item.title}}</li>
				</ul>
			</li>
			<li v-show="searchNum == 3">
				<div class="condition-filter">
					<div class="condition-filter-title">课程类型</div>
					<ul>
						<li v-for="item in courseType" :class="item.active?'active':''">{{item.title}}</li>
					</ul>
				</div>
				<div class="condition-filter">
					<div class="condition-filter-title">学员分类</div>
					<ul>
						<li v-for="item in memberTypeList" :class="item.active?'active':''">{{item.title}}</li>
					</ul>
				</div>
				<div class="condition-bottom">
					<button type="default" class="left-btn">重置</button>
					<button type="default" class="right-btn">确定</button>
				</div>
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
		<uni-popup ref="popup" type="bottom" @change="popChange">底部弹出 Popup</uni-popup>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				menu: ['课程专业', '排序方式', '条件筛选'],
				searchNum: 0,
				courseList: [{
					subjectId: 0,
					subjectName: '全部',
					active: true
				}, {
					subjectId: 1,
					subjectName: '小学',
					active: false
				}, {
					subjectId: 2,
					subjectName: '初中',
					active: false
				}, {
					subjectId: 3,
					subjectName: '高中',
					active: false
				}, {
					subjectId: 4,
					subjectName: '职高',
					active: false
				}, {
					subjectId: 5,
					subjectName: '学前',
					active: false
				}, {
					subjectId: 4,
					subjectName: '职高',
					active: false
				}, {
					subjectId: 5,
					subjectName: '学前',
					active: false
				}],
				orderShow: [{
						title: "综合排序",
						key: "BYGONE",
						active: true
					},
					{
						title: "最新",
						key: "NEW",
						active: false
					},
					{
						title: "最热",
						key: "FOLLOW",
						active: false
					},
					{
						title: "学分从低到高",
						key: "ASCENDING",
						active: false
					},
					{
						title: "学分从高到低",
						key: "DESCENDING",
						active: false
					}
				],
				courseType: [{
					title: '录播课程',
					key: 'PACKAGE',
					active: true
				}, {
					title: '课程集',
					key: 'true',
					active: false
				}],
				memberTypeList: [{
					title: '全部',
					active: true
				}, {
					title: '一年级',
					active: false
				}, {
					title: '二年级',
					active: false
				}, {
					title: '三年级',
					active: false
				}],
				allCouList: [{
					courseName: '8月22号小周末线上学习'
				}, {
					courseName: '8月22号小周末线上学习'
				}, {
					courseName: '8月22号小周末线上学习'
				}, {
					courseName: '8月22号小周末线上学习'
				}, {
					courseName: '8月22号小周末线上学习'
				}, ]
			}
		},
		onLoad() {

		},
		methods: {
			showDiloag(index) {
				this.searchNum = index + 1
				this.$refs.popup.open()
			},
			popChange(e) {
				if (!e.show) {
					this.searchNum = 0
				}
			}
		}
	}
</script>

<style lang="scss">
	.course {
		display: flex;
		position: relative;
		z-index: 998;
	}

	.course>li {
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
		border-left: 12rpx solid transparent;
		border-right: 12rpx solid transparent;
		border-top: 12rpx solid #bbb;
		margin-left: 8rpx;
	}

	.course-item-wrap {
		display: flex;
	}

	.course-ul>li {
		border-bottom: 1px solid #E9E9E9;
		padding: 20rpx 0;
		position: relative;
	}

	.course-img {
		width: 253rpx;
		height: 141rpx;
		margin: 0 20rpx;
		overflow: hidden;
	}

	.course-img>image {
		width: 100%;
		height: 100%;
	}

	.course-title {
		font-size: 32rpx;
	}

	.filter-wrap {
		position: absolute;
		display: flex;
		background: #eee;
		overflow: auto;
		width: 100%;
		max-height: 550rpx;
		z-index: 998;
	}

	.filter-wrap>li {
		width: 100%;
	}

	.subject-wrap>li {
		height: 90rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.subject-wrap>li.active {
		background: #fff;
	}

	.condition-filter-title {
		height: 80rpx;
		line-height: 80rpx;
		text-align: left;
		margin-left: 20rpx;
	}

	.condition-filter {
		border-bottom: 1px dashed #ddd;
		margin-bottom: 20rpx;
	}

	.condition-filter>ul {
		display: flex;
		flex-wrap: wrap;
		justify-content: flex-start;
	}

	.condition-filter>ul>li {
		color: #666;
		margin: 0 0 10rpx 20rpx;
		height: 50rpx;
		line-height: 47rpx;
		padding: 0 10px;
		background: #fff;
		border-radius: 4px;
		border: 1px solid transparent;
		text-align: center;
	}

	.condition-filter>ul>li.active {
		background: #ffd7ca;
		border: 1px solid #ff662f;
		color: #ff662f;
	}

	.condition-bottom {
		display: flex;
		justify-content: flex-end;
	}

	.condition-btn {
		margin: 5rpx 20rpx 20rpx 0;
		padding: 0 20px;
		font-size: 12px;
	}

	.left-btn {
		@extend .condition-btn;
		background: #ffd7ca;
		border: 1px solid #ff662f;
		color: #ff662f;
	}

	.right-btn {
		@extend .condition-btn;
		border: 1px solid #ff662f;
		color: #fff;
		background: #ff662f;
	}
</style>

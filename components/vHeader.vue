<template>
	<view class="header">
		<view class="title">天马智慧工地管理信息看板</view>
		<view class="text">SMART ATTENDANCE BOARD</view>
		<view class="right">
			<view class="time">{{ time }}</view>
			<view class="day">{{ day }}</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			time: '',
			day: '',
			Interval: ''
		};
	},
	created() {
		this.Interval = setInterval(() => {
			this.initTime();
		}, 1000);
	},
	deactivated() {
		clearInterval(this.Interval);
	},
	methods: {
		initTime() {
			const arr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六']
			const date = new Date();
			const h = date.getHours() < 10 ? '0' + date.getHours() : date.getHours();
			const m = date.getMinutes() < 10 ? '0' + date.getMinutes() : date.getMinutes();
			const s = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds();
			const y = date.getFullYear()
			const M = date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1;
			const d = date.getDate() < 10 ? '0' + date.getDate() : date.getDate();
			const time = h + ':' + m + ':' + s;
			const mon = arr[date.getDay()];
			const day = y + '-' + M + '-' + d
			this.time = time;
			this.day = day + '   ' + mon;
		}
	}
};
</script>

<style scoped lang="scss">
.header {
	width: 100%;
	height: 50rpx;
	text-align: center;
	color: #2ef8ff;
	position: relative;
	.title {
		font-size: 16rpx;
		margin: 6rpx 0;
	}
	.text{
		font-size: 6rpx;
	}
	.right {
		position: absolute;
		width: 100rpx;
		right: 0;
		top: 0;
		.time {
			font-size: 19rpx;
			font-family: 'b';
		}
		.day {
			font-size: 8rpx;
		}
	}
}
</style>

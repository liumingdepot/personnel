<template>
	<view class="sider">
		<view class="sider-item" v-for="(item, index) of PersonImg" :key="index"  :class="'margin' + index" >
			<view class="img">
				<view class="img-item1 img-item">
					<image v-if="item.recordImage" :src="item.recordImage" mode="aspectFill"></image>
				</view>
				<view class="img-item2 img-item">
					<image v-if="item.personImage"  :src="item.personImage" mode="aspectFill"></image>
				</view>
			</view>
			<view class="foot">
				<view class="status" :style="{color:item.openResult == '成功'?'#82ff45':''}" v-if="item.openResult">{{ item.openResult == '成功' ? '识别成功!':item.openResult }}</view>
				<view class="name" v-if="item.personName">{{ item.personName||"" }}</view>
				<view class="date" v-if="item.swingTime">{{ item.swingTime||"" }}</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			PersonImg: [,,,,,,],
			Interval: null
		};
	},
	created() {
		this.getAttendancePersonImg();
		this.Interval = setInterval(() => {
			this.getAttendancePersonImg();
		}, 1000 * 10);
	},
	deactivated() {
		clearInterval(this.Interval);
	},
	methods: {
		getAttendancePersonImg() {
			uni.request({
				url: 'http://113.140.66.229:11016/visualzation/getAttendancePersonImg',
				method: 'post',
				success: res => {
					this.PersonImg = res.data.data;
				}
			});
		}
	}
};
</script>

<style scoped lang="scss">
.sider {
	float: right;
	width: 320rpx;
	height: 320rpx;
	.sider-item {
		width: 156rpx;
		height: 100rpx;
		background: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAZMAAAECCAYAAAA7JjqHAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwOC8wMy8yMA2xZGsAAAAcdEVYdFNvZnR3YXJlAEFkb2JlIEZpcmV3b3JrcyBDUzbovLKMAAAEG0lEQVR4nO3XPS6EUQCG0TtCqEahIDQqiURHohiJDahtwXqUtqCzh2kk7MEG7EGlQTKJJ4yfc+pbvMn9bp58k/Xd2eYY42gAwCetjjGOTq7m80UHH27Onr9hz7+wf3q5tewNT/e37+7z+Gq+9F38LI9v3v3GdHtt5/B8uqw9rz76fvka073jtYOL64V3vvIdYwD428QEgExMAMgm67uz2RjjbtlDAPi9/JkAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkAmZgAkIkJAJmYAJCJCQCZmACQiQkA2QtM3BYzUOQ34QAAAABJRU5ErkJggg==');
		background-repeat: no-repeat;
		background-size: 156rpx 100rpx;
		.img{
			padding: 5rpx;
			.img-item{
				width: 70rpx;
				height: 70rpx;
				background-color: #0e2959;
				image{
					width: 100%;
					height: 100%;
				}
			}
			.img-item1{
				float: left;
			}
			.img-item2{
				float: right;
			}
		}
		.foot{
			padding: 5rpx;
			font-size: 8rpx;
			line-height: 24rpx;
			color: #2ef8ff;
			.status{
				float: left;
			}
			.name{
				float: left;
				padding-left: 4rpx;
			}
			.date{
				float: right;
			}
		}
	}

	.margin0,
	.margin2,
	.margin4{
		float: left;
		margin-right: 8rpx;
		margin-bottom: 10rpx;
	}
	.margin1,
	.margin3,
	.margin5{
		float: left;
		margin-bottom: 10rpx;
	}
}
</style>

<template>
	<view class="news-box">
		<view class="prc">
			<image src="../../static/images/0.jpg" mode="aspectFill" />
		</view>
		<view class="text">
			<view class="title"
				>标撒的发生撒的发生的第三方撒打发第三方大沙发斯蒂芬的题</view
			>
			<view class="info">
				<text>信息</text>
				<text>890浏览</text>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	name: "newsbox",
	data() {
		return {};
	},
};
</script>

<style lang="scss">
.news-box {
	display: flex;
	.prc {
		width: 230rpx;
		height: 160rpx;
		overflow: hidden;
		border-radius: 10rpx;
		.image {
			width: 100%;
			height: 100%;
		}
	}
	.text {
		flex: 1;
		padding-left: 20rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		.title {
			font-size: 40rpx;
			color: #333;
			margin-bottom: 10rpx;
			text-overflow: -0- ellipsis- lastline;
			overflow: hidden;
			//溢出内容隐藏
			text-overflow: ellipsis;
			display: -webkit-box;
			//特别显示模式
			-webkit-line-clamp: 2;
			line-clamp: 2;
			-webkit-box-orient: vertical;
			// 盒子中内容竖直排列

			text {
				padding-right: 30rpx;
			}
		}
		.info {
			display: flex;
			justify-content: space-between;
			font-size: 30rpx;
			color: #999;
			margin-bottom: 10rpx;
		}
	}
}
</style>

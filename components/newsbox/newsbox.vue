<template>
	<view class="news-box">
		<view class="prc">
			<image :src="item.picurl" mode="aspectFit" />
		</view>
		<view class="text">
			<view class="title">{{ item.title }}</view>
			<view class="info" v-if="!item.looktime">
				<text>{{ item.author }}</text>
				<text>{{ item.hits }}浏览</text>
			</view>
			<view class="info" v-else>
				<text>浏览时间：{{ item.looktime }}</text>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	name: "newsbox",
	props: {
		item: {
			type: Object,
			default: () => {
				return {
					title: "默认标题",
					author: "名字",
					hits: 123,
					picurl: "../../static/images/nopic.jpg",
				};
			},
		},
	},
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
		margin-top: 10rpx;
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
			width: 90%;
		}
	}
}
</style>

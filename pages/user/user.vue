<template>
	<view>
		<view class="user">
			<view class="top">
				<image
					src="../../static/images/history.png"
					mode="aspectFit"
				/>
				<div class="text">浏览历史</div>
			</view>
		</view>
		<view class="content">
			<div class="row" v-for="item in 10">
				<newsbox 
				@click.native="newsInfo"
				:item="{title:'user标题',looktime:'2020-01-01'}"></newsbox>
			</div>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {};
	},
	methods: {
		newsInfo() {
			uni.navigateTo({
				url: "/pages/news/newsinfo",
			});
		},
	},
};
</script>

<style lang="scss" scoped>
.user {
	.top {
		padding: 50rpx 0;
		background-color: #f8f8f8;
		color: #555;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		image{
			width: 150rpx;
			height: 150rpx;
		}
		.image {
			width: 80rpx;
			height: 80rpx;
			border-radius: 50%;
		}
		.text {
			font-size: 38rpx;
			color: #333;
			margin-left: 20rpx;
		}
	}
}
.row{
	padding: 15rpx 0 !important;
	border-bottom: 1px dotted #efefef;
}
</style>

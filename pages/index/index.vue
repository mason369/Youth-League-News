<template>
	<view class="home">
		<scroll-view scroll-x class="nav-scroll">
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
			<view class="item">国内</view>
		</scroll-view>
		<view class="content">
			<view class="row" v-for="item in 10">
				<newsbox :item="{title:'首页标题',author:'李四',hits:'123'}"></newsbox>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: "Hello",
		};
	},
	onLoad() {},
	methods: {},
};
</script>

<style lang="scss" scope>
.home {
	.nav-scroll {
		height: 100rpx;
		background-color: #f7f8fa;
		white-space: nowrap;
		// 取消滚动条
		/deep/ ::-webkit-scrollbar {
			width: 4px !important;
			height: 1px !important ;
			overflow: auto !important;
			background: transparent !important ;
			-webkit-appearance: auto !important;
			display: block;
		}
		.item {
			display: inline-block;
			padding: 0 30rpx;
			line-height: 100rpx;
			font-size: 40rpx;
			color: #333;
		}
	}
	.content {
		padding: 30rpx;
		.row {
			border-bottom: 1px dotted #efefef;
			padding: 15rpx 0;
		}
	}
}
</style>

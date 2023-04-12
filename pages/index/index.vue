<template>
	<view class="home">
		<scroll-view scroll-x class="nav-scroll">
			<view
				class="item"
				:class="index === navIndex ? 'active' : ''"
				v-for="(item,index) in 10"
				@click="clickNav(index)"
				:key="index"
				>国内</view
			>
		</scroll-view>
		<view class="content">
			<view class="row" v-for="item in 10">
				<newsbox
					:item="{ title: '首页标题', author: '李四', hits: '123' }"
				></newsbox>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: "Hello",
			navIndex: 0,
		};
	},
	onLoad() {},
	methods: {
		clickNav(index) {
			this.navIndex = index;
		},
	},
};
</script>

<style lang="scss" scope>
.home {
	.nav-scroll {
		height: 100rpx;
		background-color: #f7f8fa;
		white-space: nowrap;
		// 添加固定定位
		position: fixed;
		top: var(--window-top);
		left: 0;
		z-index: 9;
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
		.active {
			color: #31c27c;
		}
	}
	.content {
		padding: 30rpx;
		padding-top: 130rpx;
		.row {
			border-bottom: 1px dotted #efefef;
			padding: 15rpx 0;
		}
	}
}
</style>

<template>
    <view class="home">
        <scroll-view scroll-x class="nav-scroll">
            <view
                class="item"
                :class="index === navIndex ? 'active' : ''"
                v-for="(item, index) in navArr"
                @click="clickNav(index,item.id)"
                :key="item.id"
                >{{ item.classname }}</view
            >
        </scroll-view>
        <view class="content">
            <view class="row" v-for="item in newsList" :key="item.id">
                <newsbox
                    @click.native="newsInfo"
                    :item="item"
                ></newsbox>
            </view>
        </view>
		<!-- 没有数据时展示 -->
		<view class="nodata" v-if="!this.newsList.length">
			<image
				src="../../static/images/nodata.png"
				mode="scaleToFill"
			/>
		</view>
    </view>
</template>

<script>
export default {
    data() {
        return {
            title: "Hello",
            navIndex: 0,
            navArr: [],
			newsList: [],
			page:1
        };
    },
    onLoad() {
        this.getNavData();
		this.getNewsList();
    },
	onReachBottom() {
		this.page++
		this.getNewsList();
	},
    methods: {
        clickNav(index,id) {
            this.navIndex = index;
			this.page = 1;
			this.newsList=[]
			this.getNewsList(id);
        },
        newsInfo() {
            uni.navigateTo({
                url: "/pages/detail/detail",
            });
        },
        // 获取导航栏列表数据
        getNavData() {
            uni.request({
                url: "https://ku.qingnian8.com/dataApi/news/navlist.php",
                data: {},
                header: {
                    Accept: "application/json",
                    "Content-Type": "application/json",
                    "X-Requested-With": "XMLHttpRequest",
                },
                method: "GET",
                sslVerify: true,
                success: ({ data, statusCode, header }) => {
                    this.navArr = data;
                    console.log(this.navArr);
                },
                fail: (error) => {},
            });
        },
		// 获取新闻列表
		getNewsList(id=50) {
			uni.request({
				url: "https://ku.qingnian8.com/dataApi/news/newslist.php",
				data: {
					cid:id,
					page:this.page
				},
				header: {
					Accept: "application/json",
					"Content-Type": "application/json",
					"X-Requested-With": "XMLHttpRequest",
				},
				method: "GET",
				sslVerify: true,
				success: ({ data, statusCode, header }) => {
					this.newsList = [...this.newsList, ...data];
					console.log(this.newsList);
				},
				fail: (error) => {},
			});
		}
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
	.nodata{
		display: flex;
		justify-content: center;
		image{
			width: 360rpx
		}
	}
}
</style>

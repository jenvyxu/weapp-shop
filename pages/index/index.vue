<template>
	<view class="wrap">
		<swiper autoplay indicator-dots="true" circular>
			<swiper-item class="swipe-item">
				<view>0</view>
			</swiper-item>
			<swiper-item class="swipe-item">
				<view>1</view>
			</swiper-item>
			<swiper-item class="swipe-item">
				<view>2</view>
			</swiper-item>
		</swiper>
		<van-divider
		  contentPosition="center"
		  customStyle="color: #ababab; font-size: 14px;"
		>
		  最热商品推荐
		</van-divider>
		<view>
			<van-grid column-num="2">
			  <van-grid-item use-slot v-for="(item, index) in goodsList" :key="index">
				 <image :src="item.url" class="good-item"/>
					<view>
						<view class="goods-title">{{item.title}}</view>
						<view class="goods-price">{{item.price | exchange}}</view>
					</view>
			  </van-grid-item>
			</van-grid>
		</view>
		<van-tabbar :active="active" active-color="#ff6366">
		  <van-tabbar-item v-for="(item, index) in tabList" :key="index"
		  :icon="item.icon"
		  @tap="changeTab(index)">{{item.text}}</van-tabbar-item>
		</van-tabbar>
	</view>
</template>

<script>
	import vanButton from '@/wxcomponents/vant/dist/button';
	import vanImage from '@/wxcomponents/vant/dist/image';
	import vanGrid from '@/wxcomponents/vant/dist/grid';
	import vanGridItem from '@/wxcomponents/vant/dist/grid-item'
	import vanTabbar from '@/wxcomponents/vant/dist/tabbar'
	import vanTabbarItem from '@/wxcomponents/vant/dist/tabbar-item'
	import vanDivider from '@/wxcomponents/vant/dist/divider'
	export default {
		data() {
			return {
				active: 0,
				tabList: [
					{
						icon: 'shop-o',
						text: '首页'
					},
					{
						icon: 'search',
						text: '分类'
					},
					{
						icon: 'shopping-cart-o',
						text: '购物车'
					},
					{
						icon: 'contact',
						text: '我'
					},					
				],
				goodsList: [
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: '稚优泉水光唇釉持久保湿不易脱色唇彩唇蜜染唇液滋润防水',
						price: 123
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: '初语童装亲子装短袖T恤母女装印花t恤休闲百搭上衣T8201310123',
						price: 190
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: 'emodues新款女装OL风格半身裙-3EMYGSG31',
						price: 400
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: '5斤包邮 正宗越南进口青芒 新鲜水果玉芒 绿色天然 生态种植',
						price: 999
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: 'emodues打底衫毛织款长袖修身百搭针织套头 -1 EMYJMM62',
						price: 888
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: '【防水防风保暖】鲨鱼皮软壳战术冲锋衣',
						price: 100
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: '5斤包邮 正宗越南进口青芒 新鲜水果玉芒 绿色天然 生态种植',
						price: 999
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: 'emodues打底衫毛织款长袖修身百搭针织套头 -1 EMYJMM62',
						price: 888
					},
					{
						url: 'https://img.yzcdn.cn/vant/cat.jpeg',
						title: '【防水防风保暖】鲨鱼皮软壳战术冲锋衣',
						price: 100
					},

				]
			}
		},
		components:{
			vanButton,
			vanImage,
			vanGrid,
			vanGridItem,
			vanTabbar,
			vanTabbarItem,
			vanDivider
		},
		onLoad() {
			console.log('page load')
		},
		methods:{
			changeTab(value) {
				this.active = value
			}
		},
		filters:{
			exchange(val) {
				return  '￥' + val
			}
		}
	}
</script>
<style scoped>
.wrap {
	background: '#eee';
}
.swipe-item{
	background-color: #f00;
	height: 60px;
}
.swipe-item:nth-child(2){
	background-color: #0f0;
}
.swipe-item:nth-child(3){
	background-color: #00f;
}

.good-item {
	object-fit: cover;
	width: 100%;
	height: 180px;
}
.goods-price{
	color: #ff525e;
	font-size: 14px;
}
.goods-title{
	font-size: 14px;
	text-overflow: ellipsis;
	line-height: 1.4em;
	height: 2.8em;
	overflow: hidden;
	word-break: break-word;

}
.goods-title::after {
	content: '...';
}
</style>

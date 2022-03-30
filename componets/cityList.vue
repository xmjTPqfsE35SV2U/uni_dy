<template>
	<view class="cityList">
		<!--  -->
		<!-- 给scroll-view要设置高度，必须设置上scroll-y或者scroll-x为true（必须要的） -->
		<!-- 只有当你的scroll-view的大小，小于其内的内容时，才有机会实现真正的滚动 -->
		<!-- 值应为某子(孙)元素id -->
		<scroll-view class="scrollCity" scroll-y="true" :scroll-into-view="alphabetId===0?'A':alphabetId">
			<view class="dw_city">
				<view class="title">
					<view class="iconfont icon-31dingwei"><text>当前城市</text></view>
					<!-- <icon class="iconfont icon-31dingwei"></icon> -->
				</view>
				<view class="dw">
					{{city_name}}
				</view>
			</view>
			<view class="re_city dw_city">
				<view class="title">
					<text>热门城市</text>
				</view>
					
				<view class="hotList">
					<view class="hot_item" v-for="item in list">
						<view>{{item}}</view>
					</view>
					
				</view>
			</view>
			<view class="city_s" v-for="item in city" :id="item.initial">
				<view class="initial">
					<view>{{item.initial}}</view>
				</view>
				<view class="city_name" v-for="items in item.list" @click="city_click(items.name)">
					{{items.name}}
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default{
		props:["city","alphabetId","city_name"],
		data(){
			return{
				list:["深圳","深圳","深圳","深圳","深圳","深圳","深圳","深圳","深圳"]
			}
		},
		//子组件没有onLoad生命周期，需要使用vue的
		created(){
		},
		//虚拟dom重新渲染并更新
		//????
		// updated() {
		// 	uni.getStorage({
		// 		key:"city_name",
		// 		success: (res) => {
		// 			this.city_name=res.data;
		// 		}
		// 	});
		// },
		watch:{
			// alphabetId(){
			// 	console.log("123");
			// 	console.log(this.alphabetId);
			// }
		},
		methods:{
			city_click(res){
				uni.setStorage({
					key:"city_name",
					data:res
				});
				// 关闭当前页，跳转到指定页
				uni.redirectTo({
					url:"/pages/changeCity/changeCity"
				});
			}
		}
		
	}
</script>

<style>
	.cityList{
		background: #000000;
		color: #FFFFFF;
		/* position: relative; */
		/* height: 600px; */
	}
	.title{
		height: 40px;
		line-height: 40px;
		/* font-size: 14px; */
	}
	.iconfont>text{
		font-size: 14px;
	}
	.dw{
		height: 30px;
		line-height: 30px;
		font-size: 14px;
		color: #aaaaaa;
	}
	.dw_city{
		padding-left: 15px;
		background-color: #222222;
		padding-bottom: 15px;
	}
	.hotList{
		font-size: 12px;
	}
	.hot_item{
		background-color: #666666;
		color: #AAAAAA;
		/* padding-left: 2.5%; */
		margin-right: 2.5%;
		margin-bottom: 10px;
		width: 30%;
		height: 25px;
		line-height: 25px;
		text-align: center;
		display: inline-block;
	}
	.city_s{
		/* background-color: #AAAAAA; */
		/* height: 38670px; */
	}
	.initial{
		padding-left: 15px;
		height: 25px;
		line-height: 25px;
		font-size: 12px;
		color: #666666;
	}
	.city_name{
		padding-left: 15px;
		height: 40px;
		line-height: 40px;
		color: #AAAAAA;	
		background-color: #222222;
		font-size: 14px;
	}
	.scrollCity{
		/* float: left; */
		/* z-index: 99; */
		/* position: absolute; */
		height: 587px;
	}
</style>

<template>
	<view class="tap">
		<navigator url="/pages/index/index" open-type="navigate">首页</navigator>
		<navigator url="/pages/follow/follow" open-type="navigate">关注</navigator>
		<view class="tap_add">
			<view class="iconfont icon-add"></view>
		</view>
		<navigator url="/pages/news/news" open-type="navigate">消息</navigator>
		<navigator url="/pages/personal/personal" open-type="navigate">我</navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.tap{
		/* display: inline-block; */
		width: 100%;
		display: flex;
		position: fixed;
		left: 0;
		bottom: 0;
		z-index: 99;
		background-color: #000000;
		/* background-color: #FFFFFF; */
	}
	.tap>view{
		height: 50px;
		line-height: 50px;
		text-align: center;
		width: 20%;
		color: #FFFFFF;
		
	}
	navigator{
		height: 50px;
		line-height: 50px;
		text-align: center;
		width: 20%;
		color: #FFFFFF;
	}
	/* tap_add{} */
	.icon-add{
		/* text-align: center; */
		margin:10px auto;
		width: 55px;
		height: 30px;
		line-height: 30px;
		border-radius: 10px;
		color: #000000;
		background-color:#FFFFFF;
	}
</style>

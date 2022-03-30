<template>
	<view class="top">
		<!-- <view class="h_temp">
		</view> -->
		<view class="img_sou iconfont icon-search"></view>
		<view class="con">
			<navigator url="/pages/index/index" open-type="navigate">推荐</navigator>
			<navigator url="/pages/city/city" open-type="navigate">同城</navigator>
		</view>
	</view>
</template>

<script>
	
</script>

<style>
	.top{
		position: fixed; /* 不脱离文档流 */
		/* text-align: center; */
		/* display: flex; */
		color: #FFFFFF;
		width: 100%;
		height: 50px;
		z-index: 99;
		/* left: 0;
		top: 0; */
		/* background-color: #000000; */
	}
	.img_sou{
		position: absolute; /* 脱离文档流 */
		height: 50px;
		line-height: 50px;
		left: 25px;
	}
	.con{
		width: 100%;
		display: flex;
		justify-content: center;
		line-height: 50px;
	}
	.con>navigator{
		margin: 0 10px;
	}
</style>

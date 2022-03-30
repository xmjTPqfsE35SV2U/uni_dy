<template>
	<view>
		<view class="header">
			<!-- <icon class="qh_img"></icon> -->
			<!-- icon ?????-->
			<navigator class="qh_img iconfont icon-quxiao" open-type="navigateBack"></navigator>
			<view class="qh_title">
				<text>切换城市</text> 
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style>
	.header{
		display: flex;
		left: 0;
		top: 0;
		background-color: #000000;
		color: #FFFFFF;
		padding-left: 15px;
	}
	.qh_img{
		z-index: 99;
		height: 80px;
		line-height: 80px;
	}
	.qh_title{
		width: 100%;
		height: 80px;
		line-height: 80px;
		margin-left: -31px;
		text-align: center;
	}
</style>

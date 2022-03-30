<template>
	<view>
		<view class="author">{{index.author}}</view>
		<view class="title">{{index.title}}</view>
		<view class="music_box">
			<view class="bg-music">@dededewwwww</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:["index"]
		
	}
</script>

<style>
	.author{
		height: 30px;
		line-height: 30px;
		font-size: 16px;
	}
	.title{
		width: 120px;
		line-height: 30px;
		font-size: 12px;
	}
	.music_box{
		width: 120px;
		overflow: hidden;
	}
	.bg-music{
		font-size: 12px;
		height: 30px;
		line-height: 30px;
		animation: music 4s infinite linear;
	}
	@keyframes music{
		from{
			transform: translate(80px);
		}
		to{
			transform: translate(-80px);
		}
	}
</style>

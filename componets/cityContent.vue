<template>
	<view class="cityContent">
		<view class="top">
			<view class="dingwei iconfont icon-31dingwei">
				自动定位：{{city_name}}
			</view>
			<navigator class="qiehuang" url="/pages/changeCity/changeCity" open-type="navigate">
				<text>切换</text>
				<view class="qiehuang_img iconfont icon-qiehuan">
				</view>
			</navigator>
		</view>
		<!--  -->
		<view class="video_list">
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
			<view class="video">
				<view>
					<video class="vp" src="../static/video/1-1.mp4"></video>
				</view>
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default{
		props:["city_name"],
		data(){
			return{
				// city_name:"北京"
			}
		}
	}
</script>

<style>
	.cityContent{
		background-color: #000000;
	}
	.top{
		color: #aaaaaa;
		float: right;
		width: 100%;
		height: 40px;
		line-height: 40px;
		margin-top: 50px;
		font-size: 14px;
	}
	.dingwei{
		font-size: 14px;
		margin-left: 15px;
		float: left;
	}
	.icon-qiehuan{
		font-size: 14px;
	}
	.qiehuang{
		/* font-size: 14px; */
		margin-right: 15px;
		float: right;
	}
	.qiehuang_img{
		display: inline-block;
	}
	.video_list{
		/* width: 100%; */
		float: left;
		background-color: #000000;
	}
	.video{
		float: left;
		width: 50%;
		position: relative;
	}
	.vp{
		margin-left: 3.75px;
		width: 180px;
	}
	.img_box{
		position: absolute;
		right: 7px;
		bottom: 10px;
	}
	.img{
		width: 30px;
		height: 30px;
		border-radius: 50%;
	}
</style>

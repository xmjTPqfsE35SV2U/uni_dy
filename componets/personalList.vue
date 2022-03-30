<template>
	<view class="personalList">
		<view class="video_box">
			<video class="video" loop="true" muted autoplay="true" :controls="false" objectFit="cover" src="../static/video/1-5.mp4"></video>
			<view class="video_icon iconfont icon-add">
				2333
			</view>
		</view>
		<view class="video_box">
			<video class="video" loop="true" muted autoplay="true" :controls="false" objectFit="cover" src="../static/video/1-5.mp4"></video>
			<view class="video_icon iconfont icon-add">
				2333
			</view>
		</view>
		<view class="video_box">
			<video class="video" loop="true" muted autoplay="true" :controls="false" objectFit="cover" src="../static/video/1-5.mp4"></video>
			<view class="video_icon iconfont icon-add">
				2333
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				personalList:[]
			}
		},
		created() {
			uni.request({
				url:"/dpc/videoData.json",
				success: (res) => {
					this.personalList=res.data.list;
					// console.log(res);
					console.log(this.personalList);
				}
			})
		}
	}
</script>

<style>
	.personalList{
		display: flex;
		color: #FFFFFF;
		padding: 0px 15px;
	}
	.video_box{
		position: relative;
		height: 120px;
		width: 33%;
	}
	.video_icon{
		position: absolute;
		font-size: 14px;
		bottom: 10px;
		left: 10px;
	}
	.video{
		height: 100%;
		width: 100%;
	}
</style>

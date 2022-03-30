<template>
	<view>
		<!-- cover保持原有尺寸比例。但部分内容可能被剪切。 -->
		<video :id="item.id+''" :controls="false" loop="true" muted class="video" objectFit="cover" :src="item.src" :autoplay="isPlay">
			<cover-view class="video_on iconfont icon-24gl-play" @click="onVideo"></cover-view>
		</video>
	</view>
</template>

<script>
	export default{
		props:["item","index"],
		data(){
			return{
				isPlay:false,
				onPlay:true
			}
		},
		created() {
			// video区分视频必须不同
			this.videoContext=uni.createVideoContext(this.item.id.toString(),this);
			// this.videoContext.play()
			console.log(this.item.id);
			if(this.index==0){
				this.isPlay=true;
				// this.onPlay=true;
				// this.videoContext.play()
			}
		},
		methods:{
			play(){
				this.videoContext.play();
				this.onPlay=true;
			},
			pause(){
				this.videoContext.pause();
				if(this.onPlay==false){
					
				}
			},
			onVideo(){
				if(this.onPlay){
					this.pause();
					this.onPlay=false;
				}else{
					this.play();
					this.onPlay=true;
				}
				
				console.log(this.onPlay);
			}
		}
	}
</script>

<style>
	.video{
		/* height: 100%; */
		position: relative;
		height: 350px;
		width: 80%;
	}
	.video_on{
		position: absolute;
		right: 10px;
		bottom: 10px;
	}
</style>

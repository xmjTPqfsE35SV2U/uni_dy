<template>
	<view class="videoPlay">
		<!-- chrome为了防止用户打开一个页面后自动播放声音很大的媒体 -->
		<video :controls="false" loop="true" :id="video" muted class="video" :src="video" @click="isPlay" :autoplay="isplays"></video>
	</view>
</template>

<script>
	export default{
		props:["video","index"],
		data() {
			return {
				plays:true,
				num:0,
				times:null,
				isplays:false
			}
		},
		created() {
			//id不能相同
			this.videoContext = uni.createVideoContext(this.video,this);
			
			//
			if(this.index.id===1){
				this.isplays=true;
				console.log(this.index.id);
			}
			// console.log(this.videoContext);
		},
		methods:{
			player(){
				
				// console.log("123");
				
				// console.log(this.videoContext);
				this.videoContext.seek(0);
				this.videoContext.play();
				this.plays=true;
			},
			pause(){
				// console.log("321");
				this.plays=false;
				this.videoContext.pause();
			},
			isPlay(){
				this.num++;
				clearTimeout(this.times);
				// console.log(this.num);
				//定时器可以在执行过程中被清除
				// 定时器同步异步？
				this.times = setTimeout(()=>{
					if(this.num<2){
						this.onPlay();
					}
					if(this.num>=2){
						//
						this.$emit("changedb");
						// console.log("222");
					}
					this.num=0;
				},300);
				// console.log(this.num);
				
			},
			onPlay(){
				this.plays=!this.plays;
				if(this.plays){
					console.log("b");
					this.videoContext.play();
				}else{
					this.pause();
					console.log("z");
				}
			},
			
		}
		// src只识别静态资源 动态加载使用require引入图片
		// created() {
		// 	console.log(this.video);
		// }
	}
	
</script>

<style>
	.videoPlay{
		width: 100%;
		height: 100%;
	}
	.video{
		width: 100%;
		height: 100%;
	}
</style>

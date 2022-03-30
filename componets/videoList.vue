<template>
	<view class="videoList">
		<swiper class="video swiper" :vertical="true" @change="swipeChange" @touchstart="touchStart" @touchend="touchEnd">
			<!-- {{list}} -->
			<swiper-item v-for="item in list" >
				<!-- 父组件嵌套的子组件中，使用v-bind:msg=‘xxxx’进行对象的绑定，子组件中通过定义props接收对应的msg对象 -->
				<video-play @changedb="changedb" ref="video" :video="item.src" :index="item"></video-play>
				<listRight @open="open" :index="item" ref="guang_z"></listRight>
				<listLeft :index="item" class="left-box"></listLeft>
			</swiper-item>
		</swiper>
		<!--  -->
		<comment @close="close" v-show="isOPen"></comment>
	</view>
</template>

<script>
	import videoPlay from "./videoPlay.vue"
	import listLeft from "./listLeft.vue"
	import listRight from "./listRight.vue"
	import comment from "./comment.vue"
	var time=null;
	var ele=null;
	export default {
		props:["list"],
		data(){
			return{
				startCurrent:0,
				endCurrent:0,
				startPageY:0,
				endPageY:0,
				isOPen:false
			}
		},
		created(){
		},
		components:{
			videoPlay,
			listLeft,
			listRight,
			comment
		},
		methods:{
			touchStart(e){
				this.startPageY=e.changedTouches[0].pageY;
				console.log(this.startPageY);
			},
			touchEnd(e){
				this.endPageY = e.changedTouches[0].pageY;
				console.log(this.endPageY);
			},
			swipeChange(res){
				this.endCurrent=res.detail.current;
				clearTimeout(time),
				time=setTimeout(()=>{
					if(this.endPageY<this.startPageY){
						console.log("s");
						this.$refs.video[this.endCurrent].player();
						this.$refs.video[this.endCurrent-1].pause();
						console.log(this.endCurrent);
						this.startPageY=0;
						this.endPageY=0;
					}
					if(this.endPageY>this.startPageY){
						console.log(this.endCurrent);
						this.$refs.video[this.endCurrent].player();
						this.$refs.video[this.endCurrent+1].pause();
						this.startPageY=0;
						this.endPageY=0;
						console.log("x");
					}
					
					// console.log(this.startCurrent);
					// if(this.endCurrent>this.startCurrent){
					// 	this.$refs.video[this.endCurrent].player();
					// 	console.log(this.endCurrent);
					// 	this.$refs.video[this.endCurrent-1].pause();
						
					// }
					// if(this.endCurrent<this.startCurrent){
					// 	console.log(this.$refs.video[this.startCurrent]);
					// 	this.$refs.video[this.endCurrent].player();
					// 	this.$refs.video[this.endCurrent+1].pause();
					// }
					// this.startCurrent=this.endCurrent;
				},1000)
				
				
			},
			changedb(id){
				// console.log(this.list);
				this.$refs.guang_z[0].guang_z();
				// this.$emit("changedbl");
			},
			open(){
				this.isOPen=true;
			},
			close(){
				this.isOPen=false;
			}
		}
	}
</script>

<style>
	.videoList>swiper{
		width: 100%;
		height: 667px;
	}
	.left-box{
		color: #FFFFFF;
		position: absolute;
		left: 10px;
		bottom: 50px;
		z-index: 99;
	}
	/* .videoList{
		width: 100%;
		height: 100%;   ?????
	} */
</style>

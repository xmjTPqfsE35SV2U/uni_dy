<template>
	<view class="right-box">
		<view class="author_img">
			<image @click="click_user" class="img" src="../static/images/user.jpeg"></image>
			<view class="guanzhu iconfont icon-add" v-show="add" @click="isAdd"></view>
		</view>
		<view class="right_tb iconfont icon-shoucang" :style="color_s" @click="isStart">		
			<view class=""></view>
		</view>
		<view class="number">{{index.loveNumber}}</view>
		<view class="right_tb iconfont icon-xiaoxi" @click="click_xiaoxi"></view>
		<view class="number">{{index.commentNumber}}</view>
		<view class="right_tb iconfont icon-fenxiang"></view>
		<view class="number">{{index.shareNumber}}</view>
		<view class="music_img">
			<!-- 图片会撑开div，给图片设置宽高使其等比例缩小 -->
			<image class="img" src="../static/images/user.jpeg"></image>
		</view>
		
		
		<!-- <view>2</view> -->
	</view>
</template>

<script>
	export default{
		props:["index"],
		data(){
			return{
				add:true,
				color_s:""
			}
		},
		methods:{
			isAdd(){
				this.add=false;
			},
			isStart(){
				
				this.color_s= (this.color_s==="" ? "color:#FF0000":"");
			},
			guang_z(){
				// console.log(id);
				// if(this.index)
				console.log(this.index);
				this.color_s="color:#FF0000";
			},
			click_user(){
				uni.navigateTo({
					url:"/pages/user/user"
				})
			},
			click_xiaoxi(){
				this.$emit("open");
			}
		}
	}
</script>

<style>
	.right-box{
		position: absolute;
		right: 10px;
		bottom: 50px;
		color: #FFFFFF;
	}
	.img{
		width: 46px;
		height: 46px;
		/* rad */
		border-radius: 50%;
		border: #404040 solid 2px;
	}
	.author_img{
		position: relative;
		height: 50px;
		margin-bottom: 15px;
		/* border-radius: 50%; */
	}
	.music_img{
		/* linear ：动画从头到尾的速度是相同的。 */
		animation: music 4s infinite linear; 
		margin-top: 12px;
		height: 50px;
	}
	.right_tb{
		/* color: #FF0000; */
		/* line-height: 40px; */
		margin-top: 5px;
		text-align: center;
		font-size: 25px;
	}
	.number{
		margin-top: 5px;
		text-align: center;
		font-size: 12px;
	}
	.guanzhu{
		position: absolute;
		left: 17px;
		bottom: -8px;
		width: 16px;
		height: 16px;
		text-align: center;
		line-height: 16px;
		border-radius: 50%;
		/* font-size: 4px; */
		background-color: #FF0000;
	}
	.icon-add{
		font-size: 12px;
	}
	@keyframes music{
		0%{
			/* transform: rotate(360deg); */
		}
		100%{
			transform: rotate(360deg);
		}
	}
</style>

<template>
	<view class="follow_box">
		<scroll-view class="scroll_box" scroll-y="true" @scroll="scroll">
			<view class="follows" v-for="(item,index) in ff_list">
				<view class="img_box">
					<image class="img" src="../static/images/user.jpeg"></image>
					<view class="author">
						{{item.author}}
					</view>
					<view class="fenxiang iconfont icon-share">
					</view>
				</view>
				<view class="title">{{item.title}}</view>
				<view class="video-box">
					<followPlay ref="player" :item="item" :index="index"></followPlay>
					<view class="music">
						<view class="music_t">@世界第一可爱</view>
					</view>
				</view>
				<view>
					<view class="left">3-21</view>
					<view class="right">
						<view class="iconfont icon-shoucang">
							<text class="ic_text">点赞</text>
						</view>
						<view class="iconfont icon-xiaoxi">
							<text class="ic_text">点赞</text>
						</view>
						<view class="iconfont icon-fenxiang">
							<text class="ic_text">点赞</text>
						</view>
					</view>
				</view>
				<view class="comment">
					<view class="comment_num">{{item.commentNumber}}人评论过</view>
					<view class="comment_box">
						<view class="iconfont icon-htmal5icon16 ic_num"></view>
						<!-- placeholder输入框为空时占位符 -->
						<input class="comment_add" placeholder="添加评论..." />
					</view>
				</view>
			</view>
		</scroll-view>
		<!--  -->
	</view>
</template>

<script>
	import followPlay from "./followPlay.vue"
	var time=null;
	export default{
		props:["ff_list"],
		components:{
			followPlay
		},
		data(){
			return{
				num:0
			}
		},
		// 
		watch:{
			personalInfoList(){
				console.log(this.personalInfoList);
				console.log("3333333");
			},
			num(){
				// console.log(this.num);
				if(this.num>=0&&this.num<=this.$refs.player.length){
					this.$refs.player[this.num].play();
					console.log("2");
				}
				if((this.num-1)>=0&&(this.num-1)<this.$refs.player.length){
					this.$refs.player[this.num-1].pause();
					console.log("1");
				}
				if((this.num+1)>=0&&(this.num+1)<this.$refs.player.length){
					console.log("3");
					this.$refs.player[this.num+1].pause();
				}
				
			}
		},
		methods:{
			scroll(e){
				clearTimeout(time);
				time=setTimeout(()=>{
					const num= parseInt((e.detail.scrollTop+180)/563);
					this.num=num;
				},100);
			}
		}
	}
</script>

<style>
	.follows{
		color: #FFFFFF;
		background-color: #000000;
		/* width: 100%; */
		/* height: 100%; */
		padding: 10px 15px;
	}
	.img{
		float: left;
		height: 25px;
		width: 25px;
		border-radius: 50%;
	}
	.img_box{
		/* float: left; */
		
		height: 25px;
		
	}
	.video-box{
		height: 100%;
	}
	.author{
		float: left;
		height: 25px;
		margin-left: 5px;
		line-height: 25px;
		font-size: 14px;
	}
	/* 当父元素的display属性为flex时，以下几种属性会失效
	1.float(浮动)会失效
	2.clear(清除)会失效
	3.text-align(文本排列)会失效 */
	.fenxiang{
		float: right;
		height: 25px;
		line-height: 25px;
		font-size: 12px;
	}
	.title{
		margin-top: 15px;
		font-size: 14px;
		height: 25px;
		line-height: 25px;
	}
	.left{
		height: 25px;
		line-height: 25px;
		float: left;
		font-size: 14px;
	}
	.right{
		margin-top: 25px;
		height: 25px;
	}
	.right>view{
		display: flex;
		justify-content: center;
		margin-left: 10px;
		height: 25px;
		line-height: 25px;
		float: right;
		font-size: 20px;
	}
	.ic_text{
		margin-left: 2px;
		font-size: 12px;
	}
	.comment_box{
		position: relative;
	}
	.comment_num{
		margin: 10px 0;
		height: 16px;
		line-height: 16px;
		font-size: 14px;
		color: #AAAAAA;
	}
	.ic_num{
		position: absolute;
		/* font-size: 14px; */
	}
	.comment_add{
		font-size: 14px;
		margin-left: 25px;
	}
	.music{
		width: 200px;
		overflow: hidden;
	}
	.music_t{
		animation: music 3s infinite;
		font-size: 14px;
	}
	@keyframes music{
		from{
			transform: translate(80px);
		}
		to{
			transform: translate(-80px);
		}
	}
	.scroll_box{
		height: 617px;
	}
	.follow_box{
		height: 100%;
		background-color: #000000;
	}
</style>

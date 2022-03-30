<template>
	<view class="follow">
		<view class="top">
			<view class="img_sou iconfont icon-xiangji">
				<view class="shuipai">随拍</view>
			</view>
			
			<view class="con">
				<navigator :class="follow_xb" url="/pages/follow/follow" open-type="redirect">关注</navigator>
				<navigator :class="friend_xb" url="/pages/friend/friend" open-type="redirect">好友</navigator>
			</view>
		</view>
		<view class="temp_h"></view>
	</view>
</template>

<script>
	export default{
		props:["page"],
		data(){
			return{
				friend_xb:"",
				follow_xb:""
			}
		},
		methods:{
			getPage(){
				if(this.page==="friend"){
					this.friend_xb="xb";
					this.follow_xb="";
				}else if(this.page==="follow"){
					this.follow_xb="xb";
					this.friend_xb="";
				}
			}
		},
		created() {
			this.getPage();
		}
		
	}
</script>

<style>
	.follow{
	}
	.top{
		position: fixed; /* 不脱离文档流 */
		display: flex;
		/* 交叉轴上如何对齐 */
		align-items: center;
		color: #FFFFFF;
		width: 100%;
		height: 50px;
		z-index: 99;
		/* background-color: #000000; */
	}
	.img_sou{
		position: absolute; /* 脱离文档流 */
		height: 50px;
		line-height: 50px;
		left: 10px;
	}
	.con{
		width: 100%;
		display: flex;
		justify-content: center;
		/* line-height: 50px; */
	}
	.con>navigator{
		margin: 0 10px;
	}
	.shuipai{
		padding-left: 5px;
		font-size: 15px;
		display: inline-block;
	}
	.temp_h{
		height: 50px;
	}
	.xb{
		/* 需要边框长度比容器小一些时,伪类在实现这个效果时很方便 */
		border-bottom: #007AFF solid 2px;
	}
</style>

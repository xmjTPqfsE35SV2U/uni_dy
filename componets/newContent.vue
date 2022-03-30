<template>
	<view class="newContent">
		<view class="item-box">
			<view class="item" v-for="item in iconList">
				<view class="img_box">
					<image class="img" :src="item.src"></image>
				</view>
				<view class="item_text">
					{{item.text}}
				</view>
			</view>
		</view>
		<!--  -->
		<view class="author_box" v-for="item in newList">
			<view class="author">
				<image class="author_img" src="../static/images/user.jpeg"></image>
			</view>
			<view class="author_xinxi">
				<view class="time">
					<view class="author_name">
						{{item.name}}
					</view>
					<view>
						{{item.time}}
					</view>
				</view>
				<view class="xinxi">
					{{item.content}}
				</view>
			</view>
		</view>
		<!--  -->
		<view class="more">
			暂无更多消息
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				newList:[
					{
						id:1,
						name:"吴",
						time:"10-3",
						content:"你好，很好信和你斗法"
					},
					{
						id:2,
						name:"吴一",
						time:"10-4",
						content:"你好，很好信和你斗法"
					},
					{
						id:3,
						name:"吴吴一",
						time:"10-5",
						content:"你好，很好信和你斗法"
					},
					{
						id:4,
						name:"吴一一",
						time:"10-7",
						content:"你好，很好信和你斗法"
					}
				],
				iconList:[
					{
						id:1,
						// 本地图片不能直接引用相对路径，需要用require引用图片地址,或者先用impiort引入图片
						src:require('../static/images/user.jpeg'),
						text:"粉丝"
					},
					{
						id:2,
						src:require('../static/images/user.jpeg'),
						text:"点赞"
					},
					{
						id:3,
						src:require('../static/images/user.jpeg'),
						text:"评论和@"
					},
					{
						id:4,
						src:require('../static/images/user.jpeg'),
						text:"随拍"
					}
				]
			}
		}
	}
</script>

<style>
	.img{
		width: 40px;
		height: 40px;
		border-radius: 5px;
	}
	.img_box{
		/* width: 100%; */
		text-align: center;
	}
	.item{
		padding-top: 20px;
		width: 25%;
	}
	.item_text{
		margin-top: 15px;
		font-size: 14px;
		color: #EEEEEE;
		text-align: center;
	}
	.item-box{
		background-color: #000000;
		display: flex;
	}
	.newContent{
		background-color: #000000;
		height: 667px;
	}
	/*  */
	.author_box{
		color: #AAAAAA;
		padding: 15px 10px;
		display: flex;
		/* justify-content: space-around; */
		
	}
	.author_img{
		margin-left: 10px;
		width: 45px;
		height: 45px;
		border-radius: 50%;
	}
	.author_xinxi{
		margin-left: 20px;
		margin-right: 20px;
		width: 100%;
	}
	.author_name{
		color: #FFFFFF;
		font-size: 14px;
	}
	.time{
		height: 25px;
		line-height: 25px;
		font-size: 12px;
		width: 100%;
		display: flex;
		justify-content: space-between;
	}
	.xinxi{
		height: 25px;
		line-height: 25px;
		font-size: 12px;
	}
	/*  */
	.more{
		color: #AAAAAA;
		text-align: center;
		height: 50px;
		line-height: 50px;
		font-size: 12px;
	}
</style>

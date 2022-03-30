<template>
	<view class="comment_box">
		<view class="comment">
			<view class="comment_title">
				<view class="icon_qx iconfont icon-quxiao" @click="close()"></view>
				<view class="comment_px">2.5w条评论</view>
			</view>
			<!--  -->
			<scroll-view class="comment_item" scroll-y="true">
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<!--  -->
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<view class="item">
					<view class="comment_author">
						<view class="author_box">
							<image class="author_img" src="../static/images/user.jpeg"></image>
							<view class="author_xinxi">
								<view class="author_name">
									异想天开
								</view>
								<view class="author_text">
									好好好好好
								</view>
							</view>
						</view>
						<view >
							<view class="icon_num iconfont icon-shoucang"></view>
							<view class="num">12</view>
						</view>
					</view>
				</view>
				<!--  -->
				<view class="comment_pinglun">
					留下评论
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default{
		methods:{
			close(){
				this.$emit("close");
			}
		}
	}
	
</script>

<style>
	.comment_box{
		width: 100%;
		/* position: relative; */
		
	}
	.comment{
		left: 0;
		bottom: 0;
		z-index: 100;
		height: 500px;
		background-color: #FFFFFF;
		width: 100%;
		/* color: #FFFFFF; */
		position: fixed;
		border-radius: 15px 15px 0 0;
	}
	.comment_title{
		height: 25px;
		line-height: 25px;
		text-align: center;
	}
	.icon_qx{
		margin-right: 15px;
		float: right;
	}
	.comment_px{
		padding-left: 15px;
	}
	/*  */
	.item{
		/* height: 50px; */
	}
	.comment_author{
		margin: 0 15px;
		margin-top: 10px;
		display: flex;
		height: 50px;
		line-height: 50px;
		justify-content: space-between;
	}
	.comment_item{
		height: 450px;
	}
	.author_img{
		height: 40px;
		width: 40px;
		border-radius: 50%;
		/* float: right; */
	}
	.author_box{
		display: flex;
	}
	.author_name{
		height: 25px;
		line-height: 25px;
	}
	.author_text{
		height: 25px;
		line-height: 25px;
		font-size: 14px;
	}
	.comment_pinglun{
		height: 50px;
		line-height: 50px;
		color: #666666;
		margin-left: 15px;
		font-size: 18px;
	}
	.icon_num{
		height: 25px;
		line-height: 25px;
		font-size: 20px;
	}
	.num{
		height: 25px;
		line-height:normal;
		text-align: center;
		font-size: 14px;
	}
</style>

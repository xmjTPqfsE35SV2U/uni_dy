<template>
	<view class="changeInfo">
		<view class="author_nav">
			<navigator open-type="navigateBack" class="author_icon iconfont icon-direction-left">
			</navigator>
			<view class="author_bianji">
				编辑个人页面
			</view>
		</view>
		<!--  -->
		<view class="author_touxiang">
			<view>
				<view class="img_box">
					<image class="img" @click="chooseImg" :src="author_img"></image>
					<view class="img_title">
						点击更换头像
					</view>
				</view>
			</view>
		</view>
		<!--  -->
		<view class="author_xinxi">
			<navigator url="/pages/modify/modify?page=name" class="author_label">
				<text class="laber_text label_left">昵称</text>
				<view class="label_right">
					<text class="laber_text">{{userName}}</text>
					<view class="icon_laber iconfont icon-qiehuan">
					</view>
				</view>
			</navigator>
			<!--  -->
			<navigator class="author_label" url="/pages/modify/modify?page=uid">
				<text class="laber_text label_left">抖音号</text>
				<view class="label_right">
					<text class="laber_text">{{userId}}</text>
					<view class="icon_laber iconfont icon-qiehuan">
					</view>
				</view>
			</navigator>
			
			<navigator url="/pages/modify/modify?page=jianjie" class="author_label">
				<text class="laber_text label_left">简介</text>
				<view class="label_right">
					<text class="laber_text">{{intrduction}}</text>
					<view class="icon_laber iconfont icon-qiehuan">
					</view>
				</view>
			</navigator>
			<picker :range="school" mode = selector @change="schoolChange">
				<view class="author_label" >
					<text class="laber_text label_left">学校</text>
					<view class="label_right">
						<text class="laber_text">{{user.school}}</text>
						<view class="icon_laber iconfont icon-qiehuan">
						</view>
					</view>
				</view>
			</picker>
			<picker :range="sex" @change="sexChange">
				<view class="author_label">
					<text class="laber_text label_left">性别</text>
					<view class="label_right">
						<text class="laber_text">{{user.sex}}</text>
						<view class="icon_laber iconfont icon-qiehuan">
						</view>
					</view>
				</view>
			</picker>
			<picker mode="date" @change="dataChange">
				<view class="author_label">
					<text class="laber_text label_left">生日</text>
					<view class="label_right">
						<text class="laber_text">{{user.birthday}}</text>
						<view class="icon_laber iconfont icon-qiehuan">
						</view>
					</view>
				</view>
			</picker>
			<picker :range="city" @change="cityChange">
				<view class="author_label">
					<text class="laber_text label_left">地区</text>
					<view class="label_right">
						<text class="laber_text">{{user.city}}</text>
						<view class="icon_laber iconfont icon-qiehuan">
						</view>
					</view>
				</view>
			</picker>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				author_img:"../../static/images/user.jpeg",
				userName:"吴一",
				userId:"123456",
				intrduction:"你好",
				user:{
					school:"北京",
					sex:"男",
					birthday:"2000-3-1",
					city:"北京"
				},
				school:["北京","清华","蓝翔"],
				sex:["男","女"],
				city:["北京","上海","广州","深圳"]
			}
		},
		onShow() {
			uni.getStorage({
				key:"user",
				success: (res) => {
					this.userName=res.data;
				}
			}),
			uni.getStorage({
				key:"userId",
				success: (res) => {
					this.userId=res.data;
				}
			}),
			uni.getStorage({
				key:"intrduction",
				success: (res) => {
					this.intrduction=res.data;
				}
			}),
			uni.getStorage({
				key:"school",
				success: (res) => {
					this.user.school=res.data;
				}
			}),
			uni.getStorage({
				key:"sex",
				success: (res) => {
					this.user.sex=res.data;
				}
			}),
			uni.getStorage({
				key:"birthday",
				success: (res) => {
					this.user.birthday=res.data;
				}
			}),
			uni.getStorage({
				key:"city",
				success: (res) => {
					this.user.city=res.data;
				}
			})
		},
		methods:{
			chooseImg(){
				uni.chooseImage({
					count:1,
					// original 原图，compressed 压缩图，默认二者都有
					sizeType:["original ","compressed"],
					// album 从相册选图，camera 使用相机，默认二者都有。
					sourceType:["album "],
					success: (res) => {
						this.author_img=res.tempFilePaths[0];
						console.log(res.tempFilePaths[0]);
					}
				})
			},
			schoolChange(res){
				this.user.school=this.school[res.target.value];
				uni.setStorage({
					key:"school",
					data:this.school[res.target.value],
					success: (res) => {
					}
				})
			},
			sexChange(res){
				this.user.sex=this.sex[res.target.value];
				uni.setStorage({
					key:"sex",
					data:this.sex[res.target.value]
				})
			},
			dataChange(res){
				this.user.birthday=res.detail.value;
				uni.setStorage({
					key:"birthday",
					data:res.detail.value
				})
			},
			cityChange(res){
				// console.log(this.city[res.target.value]);
				this.user.city=this.city[res.target.value];
				uni.setStorage({
					key:"city",
					data:this.city[res.target.value]
				})
			}
		}
	}
</script>

<style>
	.changeInfo{
		color: #FFFFFF;
		background-color: #000000;
		height: 667px;
		position: relative;
	}
	.author_icon{
		position: absolute;
		top: 17px;
		left: 10px;
	}
	.author_nav{
			height: 50px;
	}
	.author_bianji{
		font-size: 18px;
		line-height: 50px;
		text-align: center;
	}
	/*  */
	.author_touxiang{
		height: 125px;
		/* line-height: 150px; */
		padding-top: 25px;
		border-top: 1px solid #333333;
		border-bottom: 1px solid #333333;
	}
	.img{
		width: 70px;
		height: 70px;
		border-radius: 50%;
	}
	.img_box{
		/* height: 150px; */
		/* line-height: 150px; */
		text-align: center;
	}
	.img_title{
		margin-top: 10px;
		color: #999999;
		font-size: 14px;
	}
	/*  */
	.author_xinxi{
		padding: 0 10px;
	}
	.laber_text{
		height: 56px;
		font-size: 14px;
		color: #999999;
		line-height: 55px;
	}
	.author_label{
		display: flex;
		justify-content: space-between;
	}
	.label_left{
		color: #FFFFFF;
	}
	.label_right{
		display: flex;
	}
	.icon_laber{
		padding-top: 20px;
		padding-left: 10px;
		/* font-size: 12px; */
	}
</style>

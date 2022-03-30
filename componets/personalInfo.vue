<template>
	<view class="personalInfo">
		<view class="bg_image_box">
			<view class="bg_image">
				<image class="img"></image>
			</view>
		</view>
		<view class="content">
			<view class="content_title">
				<view class="author_img_box">
					<image class="author_img" src="../static/images/user.jpeg"></image>
				</view>
				<!--  -->
				<view v-if="page=='personal'" class="author_label">
					<view class="author_bj" @click="changeInfo">
						编辑资料
					</view>
				</view>
				<view v-if="page=='user'" class="author_label">
					<view class="author_bj" :style="bg_guanzhu" @click="click_guanzhu">
						<view :class="icon_guanzhu">{{guanzhu_text}}</view>
					</view>
				</view>
			</view>
			<!--  -->
			<view class="content_text">
				<view class="author_text">
					<view class="author_name">
						{{userName}}
					</view>
					<view class="author_id">
						抖音号：12345678
					</view>
				</view>
				<view class="live">
					<view class="live_text">
						我不爱睡觉
					</view>
					<view class="live_label">
						家里蹲大学
					</view>
					<view class="live_label">
						家里蹲大学
					</view>
				</view>
			</view>
			<!--  -->
			<view class="content_label">
				<view class="label_dianzan label_g">
					<text class="label_number">0</text>
					<text class="laber_text">获赞</text>
				</view>
				<view class="label_guangzhu label_g">
					<text class="label_number">38</text>
					<text class="laber_text">关注</text>
					
				</view>
				<view class="label_fensi label_g">
					<text class="label_number">9</text>
					<text class="laber_text">粉丝</text>
				</view>
			</view>
			<!--  -->
			<view class="content_paizhao">
				<view class="paizhao iconfont icon-xiangji">
					添加拍照
				</view>
			</view>
			<!--  -->
			<view class="content_tag">
				<view class="zuoping" :style="boder_zp" @click="tag_b('zp')">作品</view>
				<view class="dongtai" :style="boder_dt" @click="tag_b('dt')">动态</view>
				<view class="xihuang" :style="boder_xh" @click="tag_b('xh')">喜欢</view>
			</view>
		</view>
		<!--  -->
		<view class="videoList">
			<personalList v-show="temp=='zp'"></personalList>
			<followList v-show="temp=='dt'" :ff_list="personalInfoList"></followList>
			<personalList v-show="temp=='xh'"></personalList>
		</view>
		<!--  -->
		<view class="more">
			没有更多了
		</view>
	</view>
</template>

<script>
	import personalList from "./personalList.vue"
	import followList from "./followList.vue"
	export default{
		props:["userName","page"],
		data(){
			return{
				boder_zp:"border-bottom: #BD2C00 solid 2px",
				boder_dt:"",
				boder_xh:"",
				personalInfoList:[],
				temp:"zp",
				bg_guanzhu:"background-color:red",
				guanzhu_text:"关注",
				icon_guanzhu:"iconfont icon-add"
			}
		},
		created() {
			console.log(this.page);
			uni.request({
				url:"/dpc/videoData.json",
				success: (res) => {
					this.personalInfoList=res.data.list;
					// console.log(this.personalInfoList);
				}
			})
		},
		
		components:{
			personalList,
			followList
		},
		methods:{
			tag_b(res){
				if(res=='zp'){
					this.boder_zp="border-bottom: #BD2C00 solid 2px";
					this.boder_xh="";
					this.boder_dt="";
					this.temp="zp"
				}
				if(res=='dt'){
					this.boder_dt="border-bottom: #BD2C00 solid 2px";
					this.boder_zp="";
					this.boder_xh="";
					this.temp="dt"
				}
				if(res=='xh'){
					this.boder_xh="border-bottom: #BD2C00 solid 2px";
					this.boder_zp="";
					this.boder_dt="";
					this.temp="xh"
				}
				// console.log(res);
			},
			changeInfo(){
				// 在起始页面跳转到
				uni.navigateTo({
					url:"/pages/changeInfo/changeInfo"
				})
			},
			click_guanzhu(){
				if(this.bg_guanzhu==""){
					this.bg_guanzhu="background-color:red";
					this.guanzhu_text="关注";
					this.icon_guanzhu="iconfont icon-add"
				}else{
					this.bg_guanzhu="";
					this.guanzhu_text="取消关注";
					this.icon_guanzhu=""
				}
			}
		}
		
	}
</script>

<style>
	.personalInfo{
		background-color: #000000;
		/* height: 667px; */
	}
	.bg_image_box{
		background-color: #000000;
	}
	.bg_image{
		/* width: 100%; */
		padding: 0px 1px;
		/* height: 200px; */
		/* background-image: url(../static/images/u=2917836211,448548514&fm=26&gp=0.jpg); */
	}
	.img{
		background-image: url(../static/images/u=2917836211,448548514&fm=26&gp=0.jpg);
		height: 100px;
		width: 100%;
	}
	/*  */
	.content{
		padding: 0px 15px;
		color: #EEEEEE;
		margin-bottom: 10px;
	}
	.content_title{
		display: flex;
		height: 80px;
	}
	.author_img{
		width: 80px;
		height: 80px;
		border-radius: 50%;
		margin-top: -20px;
		/* margin-left: 10px; */
		border: #000000 solid 4px;
	}
	.author_label{
		margin-top: 20px;
		width: 50%;
		margin-left: 20px;
	}
	.author_bj{
		background-color: #333333;
		height: 35px;
		line-height: 35px;
		/* width: 120px; */
		width: 100%;
		text-align: center;
		border-radius: 2px;
	}
	
	.author_name{
		font-size: 24px;
		height: 50px;
		line-height: 50px;
	}
	.author_id{
		font-size: 16px;
		height: 25px;
		line-height: 25px;
	}
	.live{
		/* font-size: 1; */
	}
	.live_text{
		margin-top: 8px;
		height: 30px;
		line-height: 30px;
		color: #EEEEEE;
		border-top: 1px solid #222222;
	}
	.live_label{
		margin-top: 5px;
		height: 20px;
		line-height: 20px;
		padding: 0 5px;
		display: inline;
		background-color: #AAAAAA;
		font-size: 14px;
		color: #333333;
		border-radius: 1px;
		margin-right: 10px;
	}
	/*  */
	.content_label{
		/* display: flex; */
		
	}
	.label_g{
		display: inline;
		height: 50px;
		line-height: 50px;
		margin-right: 5px;
	}
	.label_number{
		color: #FFFFFF;
		font-size: 14px;
	}
	.laber_text{
		color: #999999;
		font-size: 14px;
	}
	/*  */
	.content_paizhao{
		/* background-color: ; */
	}
	.paizhao{
		height: 40px;
		background-color: #333333;
		line-height: 40px;
		text-align: center;
		border-radius: 3px;
		font-size: 14px;
	}
	.content_tag{
		height: 50px;
		line-height: 50px;
		color: #999999;
		display: flex;
		justify-content: space-around;
	}
	.content_tag>view{
		width: 33%;
		text-align: center;
	}
	.more{
		color: #999999;
		text-align: center;
		height: 30px;
		line-height: 30px;
		font-size: 12px;
		padding-bottom: 50px;
	}
</style>

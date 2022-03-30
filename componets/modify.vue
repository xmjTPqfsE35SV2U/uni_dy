<template>
	<view class="modify">
		<view class="author_nav">
			<navigator open-type="navigateBack" class="author_icon iconfont icon-direction-left">
			</navigator>
			<view class="author_bianji">
				{{title}}
			</view>
		</view>
		<view class="xiugai_box">
			<view class="name">
				{{content}}
			</view>
			<view v-if="page=='name'">
				<view class="input_name">
					<view class="icon_qx iconfont icon-quxiao" @click="clear('name')"></view>
					<input class="input_text" v-model="newName" maxlength="20" placeholder="输入昵称"  />
				</view>
				<view class="max_num">
					{{newName.length}}/20
				</view>
				<!--  -->
				<view class="btn_baocun" @click="click_baocun(newName)">
					保存
				</view>
			</view>
			<view v-if="page=='uid'">
				<view class="input_name">
					<view class="icon_qx iconfont icon-quxiao" @click="clear('id')"></view>
					<input class="input_text" v-model="newId" maxlength="16" />
				</view>
				<view class="max_num">
					最多16个字只允许字母，数字，下滑线，30天只能修改一次
				</view>
				<!--  -->
				<view class="btn_baocun" @click="click_baocun(newId)">
					保存
				</view>
			</view>
			<!-- jianjie -->
			<view v-if="page=='jianjie'">
				<textarea placeholder="填写个人简介" v-model="intrductionText" class="text_area"></textarea>
				<!-- <view class="max_num">
					{{newName.length}}/20
				</view> -->
				<!--  -->
				<view class="btn_baocun" @click="click_baocun(intrductionText)">
					保存
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:["page"],
		data(){
			return{
				newName:"",
				newId:"",
				title:"",
				content:"我的昵称",
				intrductionText:""
			}
		},
		created(){
			if(this.page=="name"){
				this.title="修改昵称",
				this.content="我的昵称"
			}else if(this.page=="uid"){
				this.title="修改抖音号",
				this.content="我的抖音号"
			}else if(this.page=="jianjie"){
				this.title="修改简介",
				this.content="个人简介"
			}		
			console.log(this.page);
		},
		methods:{
			click_baocun(res){
				if(this.page=="name"){
					uni.setStorage({
						key:"user",
						data:res
					})
				}else if(this.page=="uid"){
					uni.setStorage({
						key:"userId",
						data:res
					})
				}else if(this.page=="jianjie"){
					uni.setStorage({
						key:"intrduction",
						data:res
					})
				}
				// console.log("123333");
				uni.navigateTo({
					url:"/pages/changeInfo/changeInfo",
					success() {
						console.log("123333");
					}
				})
			},
			clear(res){
				if(res=="name"){
					this.newName=""
				}
				if(res=="id"){
					this.newId=""
				}
				// console.log(res);
			}
		}
	}
</script>

<style>
	.modify{
		height: 667px;
		background-color: #000000;
		color: #FFFFFF;
	}
	.author_nav{
		height: 50px;
	}
	.author_bianji{
		font-size: 18px;
		line-height: 50px;
		text-align: center;
	}
	.author_icon{
		position: absolute;
		top: 17px;
		left: 10px;
	}
	/*  */
	.name{
		font-size: 15px;
	}
	.xiugai_box{
		color: #999999;
		padding: 15px;
	}
	.icon_qx{
		font-size: 22px;
		float: right;
	}
	.input_name{
		color: #FFFFFF;
		margin-top: 5px;
		height: 50px;
		line-height: 50px;
	}
	.input_text{
		height: 50px;
		line-height: 50px;
		overflow: hidden;
	}
	.max_num{
		font-size: 12px;
	}
	/*  */
	.btn_baocun{
		height: 40px;
		line-height: 40px;
		text-align: center;
		font-size: 16px;
		color: #FFFFFF;
		background-color: #333333;
		margin-top: 50px;
		border-radius: 3px;
	}
	.text_area{
		width: 100%;
		/* padding-top: 10px; */
		margin-top: 10px;
		color: #FFFFFF;
		background-color: #333333;
	}
</style>

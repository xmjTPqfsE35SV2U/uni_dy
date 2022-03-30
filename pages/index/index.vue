<template>
	<view class="content">
		<top></top>
		<videoList @changedbl="changedbl" :list="list"></videoList>
		<navTap></navTap>
	</view>
</template>

<script>
	
	import navTap from "../../componets/navTap.vue"
	import top from "../../componets/top.vue"
	import videoList from "../../componets/videoList.vue"

	export default {
		data() {
			return {
				list:[],
				title: 'Hello'
			}
		},
		onLoad() {
			this.getVideos();
			
		},
		methods: {
			getVideos(){
				uni.request({   //异步加载    ?????????
					url:"/dpc/videoData.json",
					success: (res) => {
						this.list=res.data.list;  //this对象
						// return res;
						// console.log(this.list);
					}
				})
			},
			// changedbl(){
			// 	// console.log(this.$refs.guang_z.guang_z());
			// 	this.$refs.guang_z.guang_z();
			// }

		},
		components:{
			navTap,
			top,
			videoList,
		}
	}
</script>

<style>
	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.content{
		/* width: 100%; */
		/* height: 620px; */
		/* background-color: #000000; */
	}
	
</style>

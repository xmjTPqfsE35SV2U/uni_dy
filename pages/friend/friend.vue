<template>
	<view class="friend">
		<followNav :page="page"></followNav>
		<follow-list :ff_list="friend_list"></follow-list>
		<nav-tap></nav-tap>
	</view>
</template>

<script>
	import followNav from "../../componets/followNav.vue"
	import navTap from "../../componets/navTap.vue"
	import followList from "../../componets/followList.vue"
	export default{
		components:{
			followNav,
			navTap,
			followList
		},
		data(){
			return{
				page:"friend",
				friend_list:[]
			}
		},
		onShow() {
			this.getList();
		},
		methods:{
			getList(){
				uni.request({
					url:"/dpc/videoData.json",
					success: (res) => {
						this.friend_list=res.data.list.slice(3,6);
						console.log(this.friend_list);
					}
				})
			}
		}
	}
</script>

<style>
	.friend{
		background-color: #000000;
	}
</style>

<template>
	<view class="follow">
		<followNav :page="page"></followNav>
		<!-- ref -->
		<follow-list :ff_list="follow_list"></follow-list>
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
				page:"follow",
				follow_list:[]
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
						this.follow_list=res.data.list.slice(0,3);
						// console.log(this.follow_list);
					}
				})
			}
		}
	}
	
</script>

<style>
	.follow{
		/* height: 667px; */
		background-color: #000000;
	}
</style>

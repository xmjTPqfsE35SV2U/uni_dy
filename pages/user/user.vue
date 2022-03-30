<template>
	<view>
		<personalInfo :page="user" :userName="userName"></personalInfo>
		<nav-tap></nav-tap>
	</view>
</template>

<script>
	import personalInfo from "../../componets/personalInfo.vue"
	import navTap from "../../componets/navTap.vue"
	export default{
		data(){
			return{
				userName:"吴一",
				user:"user"
			}
		},
		components:{
			navTap,
			personalInfo
		},
		// onLoad() {
			
		// }
		onShow() {
			uni.getStorage({
				key:"user",
				success: (res) => {
					this.userName=res.data;
					// console.log(res.data);
				}
			})
		},
		methods:{
			
		}
	}
</script>

<style>
</style>

<template>
	<view>
		<personalInfo :page="personal" :userName="userName"></personalInfo>
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
				personal:"personal"
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

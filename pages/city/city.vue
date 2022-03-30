<template>
	<view class="city">
		<top></top>
		<cityContent :city_name="city_name"></cityContent>
		<nav-tap></nav-tap>
	</view>
</template>

<script>
	import navTap from "../../componets/navTap.vue"
	import top from "../../componets/top.vue"
	import cityContent from "../../componets/cityContent.vue"
	export default{
		data(){
			return{
				city_name:"北京"
			}
		},
		components:{
			cityContent,
			navTap,
			top
		},
		onShow() {
			uni.getStorage({
				key:"city_name",
				success: (res) => {
					this.city_name=res.data;
					console.log(this.city_name);
				}
			});
		}
	}
</script>
	
<style>
	.city{
		/* color: #FFFFFF; */
		width: 100%;
		height: 667px;
		background-color: #000000;
	}
</style>

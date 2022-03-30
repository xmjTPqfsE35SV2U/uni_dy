<template>
	<view>
		<newsNav></newsNav>
		<newContent></newContent>
		<navTap></navTap>
	</view>
</template>

<script>
	import newsNav from "../../componets/newsNav.vue"
	import navTap from "../../componets/navTap.vue"
	import newContent from "../../componets/newContent.vue"
	export default{
		components:{
			newsNav,
			navTap,
			newContent
		}
	}
</script>

<style>
</style>

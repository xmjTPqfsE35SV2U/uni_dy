<template>
	<view>
		<modify :page="page"></modify>
	</view>
</template>

<script>
	import modify from "../../componets/modify.vue"
	export default{
		data(){
			return{
				page:""
			}
		},
		components:{
			modify,
		},
		onLoad(res) {
			this.page=res.page;
		}
	}
</script>

<style>
</style>

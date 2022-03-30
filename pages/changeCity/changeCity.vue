<template>
	<view class="changeCity">
		<changeHeader></changeHeader>
		<city-list :city_name="city_name" :alphabetId="alphabetId" :city="citys"></city-list>
		<changeAlphabet :city="citys" @onAlphabet="onAlphabet"></changeAlphabet>
	</view>
</template>

<script>
	import changeHeader from "../../componets/changeHeader.vue"
	import cityList from "../../componets/cityList.vue"
	import changeAlphabet from "../../componets/changeAlphabet.vue"
	export default{
		data(){
			return{
				citys:[],
				alphabetId:0,
				city_name:"北京"
			}
		},
		components:{
			changeHeader,
			cityList,
			changeAlphabet
		},
		created() {
			this.getCityList();
		},
		onShow() {
			uni.getStorage({
				key:"city_name",
				success: (res) => {
					this.city_name=res.data;
					// console.log(this.city_name);
				}
			});
		},
		methods:{
			getCityList(){
				uni.request({
					url:"/dpc/city.json",
					success: (res) => {
						this.citys=res.data.city;
						// console.log(this.citys);	
					}
				})
			},
			onAlphabet(res){
				this.alphabetId=res;
				// console.log(res);
			}
		}
	}
</script>

<style>
	.changeCity{
		background-color: #000000;
	}
</style>

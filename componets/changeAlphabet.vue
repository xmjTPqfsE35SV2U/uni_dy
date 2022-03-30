<template>
	<view class="changeAlphabet" @touchmove="touchMove">
		<!-- 可以用 hover-class 属性来指定元素的点击态效果 -->
		<view class="alphabet" v-for="item in city" hover-class="hover" @click="click(item.initial)">
			{{item.initial}}
		</view>
	</view>
</template>

<script>
	var timer =null;
	export default{
		props:["city"],
		data(){
			return{
			}
		},
		methods:{
			click(res){
				this.$emit("onAlphabet",res);
				// console.log(res);
			},
			touchMove(e){
				//对于整个页面来说，包括了被卷去的body部分的长度
				// console.log(e.touches[0].pageX);
				//点击位置距离当前body可视区域的x，y坐标
				// console.log(e.touches[0].clientX-160/16);
				//定时器避免重复执行
				clearTimeout(timer);
				this.timer = setTimeout(()=>{
					const temp = e.touches[0].clientY-160;
					const touchY=parseInt(temp/16).toString();
					if(temp>=0&&temp<=352){
						this.$emit("onAlphabet",this.city[touchY].initial);
					}
				},30);
			}
		}
	}
	
</script>

<style>
	.changeAlphabet{
		width: 16px;
		position: fixed;
		top: 160px;
		right: 3px;
		text-align: center;
		color: #FFFFFF;
	}
	.alphabet{
		font-size: 12px;
		
	}
	.hover{
		font-size: 16px;
	}
</style>

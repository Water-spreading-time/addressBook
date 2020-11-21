<template>
	<view class="searchView" :style="{padding:searchViewPadding + 'upx'}">
		<view class="search flx" :style="{height:inputHeight + 'upx'}">
			<image src="../../static/search.png" mode="widthFix"></image>
			<text>搜索</text>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			searchViewPadding:{
				type:Number,
				default(){
					return 20
				}
			},
			inputHeight:{
				type:Number,
				default(){
					return 80
				}
			}
		}
	}
</script>

<style lang="less" scoped>
	.searchView{
		background: #EEEEEE;
		position: fixed;
		left:0;
		right:0;
		z-index: 999;
		/* #ifdef H5*/
		 top:44px;
		/* #endif*/
		/* #ifndef H5*/
		 top:0;
		/* #endif*/
		.search{
			background: #fff;
			align-items: center;
			justify-content: center;
			border-radius: 4px;
			font-size:32upx;
			color:#C8C7C7;
			image{
				width:40upx;
				margin-right: 20upx;
			}
		}
	}
</style>

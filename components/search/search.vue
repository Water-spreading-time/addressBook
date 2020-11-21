<template>
	<view class="searchView" :style="{padding:searchViewPadding + 'upx'}">
		<view class="inputView rel">
			<input type="text" v-model="searchVal" class="search flx searchInput" :style="{height:inputHeight + 'upx',textAlign:textAlign}" :focus="focus"/>
			<view class="flx abs fakeSearch search" :style="{height:inputHeight + 'upx',textAlign:textAlign}" @tap="search" v-show="showSearchFade">
				<image src="../../static/search.png" mode="widthFix"></image>
				<text>{{plaWarn}}</text>
			</view>
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
			},
			plaWarn:{
				type:String,
				default(){
					return "搜索"
				}
			},
			textAlign:{
				type:String,
				default(){
					return "left"
				}
			}
		},
		data(){
			return {
				searchVal:"",
				showSearchFade:true,
				focus:false
			}
		},
		methods:{
			search(){
				this.showSearchFade = false
				this.focus = true
			}
		},
		watch:{
			searchVal(val){
				this.$emit('searchValChange',val)
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
		.inputView{
			.search{
				align-items: center;
				justify-content: center;
				border-radius: 4px;
				font-size:32upx;
				color:#C8C7C7;
			}
			.searchInput{
				padding-left:40px;
				background: #fff;
				background-image:url(../../static/search.png);
				background-repeat:no-repeat;
				background-position: 10px center;
				background-size: 40upx;
			}
			.fakeSearch{
				top:0;
				left:0;
				width:100%;
				background: #fff;
			}
			image{
				width:40upx;
				margin-right: 20upx;
			}
		}
	}
</style>

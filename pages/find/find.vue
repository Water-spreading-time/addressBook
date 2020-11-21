<template>
	<view class="content">
		<jump-search/>
		
		<view class="moduleList">
			
		</view>
	</view>
</template>

<script>
	import JumpSearch from '../../components/jumpSearch/jumpSearch'
		
	export default{
		components:{JumpSearch},
		data(){
			return {
				
			}
		}
	}
</script>

<style lang="less" scoped>
	.moduleList{
		margin-top: 120upx;
	}
</style>

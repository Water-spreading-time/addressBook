<template>
	<view class="content">
		<jump-search @searchValChange="searchValChange"></jump-search>
		<!-- 通讯录导航 -->
		<address-book :bookList="bookList" :letter="letter">
			<template v-slot:addressBookList>
				<view class="bookList">
					<block v-for="item in bookList" :key="item.key">
						<view class="bookKey">{{item.key}}</view>
						<block v-for="items in item.list" :key="items.id">
							<view class="book flx" @tap="jump(items.id,items.username)">
								<view class="headimg">
									<image :src="items.headImg" mode="widthFix"></image>
								</view>
								<view class="font30 bold name">{{items.username}}</view>
							</view>
						</block>
					</block>
				</view>
			</template>
		</address-book>
	</view>
</template>

<script>
	import JumpSearch from '../../components/jumpSearch/jumpSearch'
	import AddressBook from '../../components/addressBookNavigation/addressBookNavigation'
	import {makePy} from '../../utils/utils'
		
	export default{
		components:{JumpSearch,AddressBook},
		data(){
			return{
				letter:["A", "B", "C", "D","E", "F", "G", "H","I", "J", "K", "L", "M", "N","O", "P", "Q", "R", "S", "T","U","V", "W", "X", "Y", "Z"],
				list:[
					{
						id:1,
						username:"a白小纯",
						headImg:"/static/headimg.png"
					},
					{
						id:2,
						username:"B罗小黑",
						headImg:"/static/headimg.png"
					},
					{
						id:3,
						username:"张楚岚",
						headImg:"/static/headimg.png"
					},
					{
						id:4,
						username:"冯宝宝",
						headImg:"/static/headimg.png"
					},
					{
						id:5,
						username:"五六七",
						headImg:"/static/headimg.png"
					},
					{
						id:11,
						username:"白月初",
						headImg:"/static/headimg.png"
					},
					{
						id:22,
						username:"王富贵",
						headImg:"/static/headimg.png"
					},
					{
						id:33,
						username:"叶修",
						headImg:"/static/headimg.png"
					},
					{
						id:44,
						username:"唐三",
						headImg:"/static/headimg.png"
					},
					{
						id:55,
						username:"林动",
						headImg:"/static/headimg.png"
					},
					{
						id:12,
						username:"魏无羡",
						headImg:"/static/headimg.png"
					},
					{
						id:23,
						username:"秦羽",
						headImg:"/static/headimg.png"
					},
					{
						id:34,
						username:"蛮吉",
						headImg:"/static/headimg.png"
					},
					{
						id:45,
						username:"荆天明",
						headImg:"/static/headimg.png"
					},
					{
						id:56,
						username:"武庚",
						headImg:"/static/headimg.png"
					}
				],
				bookList:[]
			}
		},
		created() {
			this.letterSrot()
		},
		methods:{
			// 对通讯录按字母顺序做排序
			letterSrot(){
				const sortList = []
				const list = this.list
				this.letter.forEach(item => {
					const obj = {}
					obj.key = item
					obj.list = []
					for(let i = 0;i < list.length;i++){
						if(item == makePy(list[i].username).substr(0,1)){
							obj.list.push(list[i])
							list.splice(i,1)
							i--
						}
					}
					if(obj.list.length)
						sortList.push(obj)
				})
				this.bookList = sortList
			},
			jump(id,name){
				console.log(`jump:id=${id},${makePy(name)}`)
			}
		},
		onNavigationBarButtonTap(){
			console.log('添加通讯录')
		}
	}
</script>

<style lang="less" scoped>
	.bookList{
		padding-left:40upx;
		.bookKey{
			padding-top:20upx;
			line-height: 60upx;
			color:#20BB5B;
		}
		.book{
			height:140upx;
			align-items: center;
			.headimg{
				width:12%;
				image{
					border-radius: 4px;
				}
			}
			.name{
				padding-left:20upx;
				line-height: 140upx;
				flex:1;
				border-bottom:1px solid #F3F3F3;
			}
		}
		.book:last-child .name{
			border-bottom:0;
		}
	}
</style>

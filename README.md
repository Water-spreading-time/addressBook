# 组件说明

**按字母顺序查找通讯录**

下载组件到工程对应目录引入组件：

`import AddressBook from '../../components/addressBookNavigation/addressBookNavigation'`

使用组件：
```
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
```

# 参数说明
| 参数                          | 类型    |  必传   | 默认值   |   单位    |           参数说明                       |
| ---------------------------   | -----:  | -----:  | -----:  | :--------|:--------------------------------------: |
| bookList                      | Array   |   true  |   无    |           |      通讯录名单列表                      |
| letter                        | Array   |   false |   [A-Z] |           |      右边索引字母列表按A-Z顺序            |
| bookKeyHeight                 | Number  |   false |   80    |    upx    |      通讯录名单首字母显示高度             |
| bookItemHeight                | Number  |   false |   140   |    upx    |      通讯录名单列表显示高度               |
| paddingRight                  | Number  |   false |   20    |    upx    |      右边索引字母右边距                   |
| searchHeight                  | Number  |   false |   120   |    upx    |      搜索框高度，没有传0                  |
| searchLetterTop               | Number  |   false |   20    |    upx    |      右边索引距离搜索框底部距离            |
| searchLetterWidth             | Number  |   false |   40    |    upx    |      右边索引显示宽度                     |
| subtractiveSearchLetterHeight | Number  |   false |   80    |    upx    |      右边索引显示总高度减去的部分          |
| tabHeight                     | Number  |   false |   50    |     px    |      底部tab高度                         |
| navHeight                     | Number  |   false |   44    |     px    |      导航栏高度                          |

# bookList格式
```
bookList:[
  {
    key:"A",
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
    ]
  }
]
```

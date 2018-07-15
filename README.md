# Vue音乐播放器webapp

## 项目截图

**推荐页，排行页，歌手页**

![推荐页，排行页，歌手页](https://github.com/wwenj/web-music-player/blob/master/screenshot/1.jpg)

**搜索页，我的本地（收藏，播放历史）**

![搜索页，我的收藏](https://github.com/wwenj/web-music-player/blob/master/screenshot/2.jpg)

**详情页，播放列表，添加歌曲到播放列表**

![搜索页，我的收藏](https://github.com/wwenj/web-music-player/blob/master/screenshot/3.jpg)

**播放页，歌词页**

![搜索页，我的收藏](https://github.com/wwenj/web-music-player/blob/master/screenshot/4.jpg)

## 项目简介

基于vue全家桶开发的一款**移动端**音乐播放器webapp，数据由qq音乐后台通过jsonp跨域和代理获取

## 技术栈

- **前端**：vue全家桶，es6，sass，axios，**jsonp**，**better-scroll**

- **数据**：qq音乐接口扒取

## 功能模块：

### 页面

1. **推荐页：** 轮播，推荐歌单，点击跳转详情组件 下3同
2. **歌手页： ** 按姓氏首字母排列，点击侧面字母栏跳转到对应歌手区域
3. **排行页：** 几种榜单，详情页显示排行数字
4. **搜索页：** 搜索框**监听**内容变化显示搜索结果，搜索结果**上拉加载**，点击搜索结果添加到当前播放列表并播放该歌曲，搜索为歌手跳转歌手详情页；保存**搜索历史**，显示**热门搜索**标签
5. **个人页：** 选项卡显示**最近播放**历史，与我的**收藏列表**
6. **播放页：**  旋转大头像，播放时间，**进度条**，上一曲下一曲，收藏，**播放模式**（单曲-顺序-随机），**歌词页**，播放按钮，迷你底部播放栏（播放页收起时显示）

### 功能

1. **播放列表：**  显示当前播放列表，查看播放模式，**清空列表**，点击收藏，点击删除，点击添加歌曲到当前播放列表
2. **添加歌曲到播放列表：** 搜索歌曲添加，播放历史添加，搜索历史添加
3. **播放组件：** 拖动进度条跳转播放进度，歌词跟随进度联动

## 架构设计

- 15个业务组件，9个基础组件
- 详情组件，歌曲列表组件，搜索框组件，scroll组件，loading组件等组件多**复用**
- **vuex集中状态管理** ：
  1. 搜索历史，收藏列表，播放历史
  2. 播放状态，播放模式，收起播放页，当前播放索引
  3. 排行榜数据，推荐歌单数据，歌手数据（进入详情页使用）
- 模块化：js模块写在assets内，数据请求模块写在api内，vuex写在mutation.js，state.js，getters.js，action.js中
- **移动端适配**：淘宝适配方案`amfe-flexible`，用sass函数统一`rem`为正常px逻辑单位
- 几种历史记录收藏列表存储在**localStorage**

## 项目测试

### 边界条件测试

- 歌曲未加载成功连续点击下一曲：设标志值，事件开始前做判断，当歌曲加载成功才能继续执行
- 选择播放歌曲当前正在播放：watch监听歌曲时，新旧值一致则不进行任何变化
- 顺序播放时播放列表中只有一首歌：判断只有一首歌时循环播放
- 删除播放列表歌曲的最后一首：关闭播放列表和播放页
- 未找到（搜索，收藏，历史等）任何数据：显示提示空信息组件
- 出现底部迷你播放页时，重新计算dom，显示正确scroll滚动位置

### 移动端测试

- 兼容：uc音乐播放器不能播放歌曲
- 滚动搜索结果出现小键盘：触摸搜索结果列表使input搜索框失焦
- 播放页收回动画卡慢：修改收回动画为改变透明度

## 项目总结

### 难点

- jsonp与代理，获取QQ音乐真实后台数据，获取数据的**二次封装**使用

- **better-scroll** 移动端插件（每次dom渲染要重新计算scroll宽度），封装成组件。

- vuex状态管理的项目结构设计

### 收获

- **业务：** 清晰项目架构，学习良好的编程风格，Es6模块化写法，Eslint代码规范，vuex状态管理，常用组件的封装复用，
- **技术：** jsonp跨域请求，vue更深入理解掌握更熟练


## 项目运行

``` bash
# 下载依赖
npm install

# serve with hot reload at localhost:8081
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

作者 [[王文健\]](http://www.wwenj.com/)  2018 年 7月 15日 
# Wisedu Mobile JavaScript SDK

金智教育移动校园 JavaScript SDK

## 安装

```
npm install bh-mobile-sdk
```

## 使用

```javascript
import {init} from 'bh-mobile-sdk'

init(() => {
    console.log(WISEDU_SDK)
})
```

从 `bh-mobile-sdk` 中引入 `init` 方法，执行成功后，在全局变量里就会有 `BH_MOBILE_SDK`

## API

SDK 提供的 Api 是分模块的，先阶段一共有三大模块，`UI, systemAbility, file`

如果想调用某个 UI 模块下的的 api，`BH_MOBILE_SDK.UI.closeWebView`

### UI

**`actionSheet(title: String, actions: Array, callback: Function)`**

系统actionSheet弹框，在页面底部弹出，一般用于多个功能选择，例如对某张图片：分享，保存图片，点赞成等

#### Arguments

1. `title: String` 弹框标题
2. `actions: Array` 弹框操作按钮的标题数组
3. `callback(index): Function(Number)` 点击按钮后的回调方法 ，会返回点击的index
    * `index: Number` 传入的按钮数据的index下标列表，从0开始

```javascript
const COUNTRY = ['中国','日本','韩国']

BH_MOBILE_SDK.UI.actionSheet('请选择', COUNTRY, (index) => {
    console.log('选择国家: ' + COUNTRY[index]);
})
```

---

**`alertView(title: String, content: String, btnTitles: Array, callback: Function)`**

系统alertView弹框，在页面正中间弹出

#### Arguments

1. `title: String` 弹框标题
2. `content: String` 弹框标题
3. `btnTitles: Array` 弹框操作按钮的标题数组
4. `callback(index): Function(Number)` 点击按钮后的回调方法 ，会返回点击的index
    * `index: Number` 传入的按钮数据的index下标列表，从0开始

```javascript
const BTNS = ['确定','取消']
BH_MOBILE_SDK.UI.alertView('提示', '这个一个alertview', BTNS, (index) => {
    console.log('点击了按钮' + BTNS[index]);
});
```

---

**`closeWebView`**

关闭当前webview

```javascript
BH_MOBILE_SDK.UI.closeWebView()
```

---

**`multiPicker`**

---

**`preViewImages(imgs: Array, [index: Number])**

原生图片浏览器，可以传递一组图片地址以及描述进行浏览，图片可以来自网络或者本地。组件默认带分享功能

#### Arguments

1. `imgs: Array` 图片数组，用于展示, 每一项的机构建下面
    * `item: Object` url 控制图片地址，desc 控制图片描述
    * url支持类型如下
        1. http地址
        2. 相对路径，相对于应用根目录，如：/image/qrcoder.png
        3. 本地绝对路径，如：通过图片选择器选择的图片路径
2. `index: Number` 默认展示哪一张，index从数组下标0开始

```javascript
BH_MOBILE_SDK.UI.preViewImages([{
  url: "http://****/1.png",
  desc: "我是图片的描述1"
}, {
  url: "http://****/2.png",
  desc: "我是图片的描述2"
}])
```

---

**`setNavHeader(flag: Boolean)`**

设置客户端原生头是否隐藏, 默认是显示的，传入 false 隐藏原生头

#### Arguments

1. `flag: Boolean` 控制头部是否显示，true: 显示, flase: 隐藏

```javascript
BH_MOBILE_SDK.UI.setNavHeader(false)
```

---

**`setTitleText(title: String)`**

设置原生头的 title

#### Arguments

1. `title: String` 头部的 title

```javascript
BH_MOBILE_SDK.UI.setTitleText('我是 title')
```

---

### social

**`share(config: Object)`**

分享内容

#### Arguments

1. `config: Object`: 分享的配置文件，title 控制分享的标题，linkUrl 控制分享的连接

分享内容

```javascript
BH_MOBILE_SDK.social.share({
    title: '分享的 title',
    linkUrl: 'http://www.baidu.com' // 分享的链接
})
```

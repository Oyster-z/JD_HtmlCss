# JD_HtmlCss
关于html和css的小项目(京东)

#### 20190627
1. 初步准备
    - css reset 初始化
    - font: 12px/1.5 (fontsize 和 fontfamily 不能省略) 这里的1.5 表示的是行高 实际高度使用字体高度 * 1.5 也就是行高 = 24px。
    - normalize.css 推荐的 css 文件，是由某组织总结的版本，保证跨浏览器之间的css 样式能保持一致

2. 搭建项目，创建文件夹, css fonts images index.html，引入ico 图标，在网址的后面加上 favicon.ico 获得当前网址的 ico图标，将ico 图片放在根目录中（引用，link href="*.ico" 文件）。
3. css 文件的准备
    - 引用normalize.css 文件到 index.html 文件中。
    - 新建 base.css/ global.css 保存公用的css文件，存储常用的css 信息。(比如版心：width: 1190px)，公共样式（头部和底部样式作为公共样式完成）。
    - 京东首页 css 文件，index.css 文件，只包含首页的css 文件。
4. 京东顶部的完成(base.css)
    - 顶栏,通栏中间有内容，内容居中对齐，a标签可点，右上角关闭。（一个盒子只给高不给宽，背景色黑色；盒子用版心居中对齐；盒子右上角有个叉号）
    ```
        // 第一个盒子的高度
        height:80px
        // 第二个盒子用版心居中对齐
        w{
            width: 1190px;
            margin: auto;
        }
        
        background: url(/../*.jpg) no-repeat;

        // 子绝父相，父亲使用relative 的方式
        i{
            width: 20px;
            height:20px;
            position:absolute;
            right: 0;
            top: 5px;
            font-family: "icomoon"
        }
    ```
    - J_event 类封装第一个盒子，给js 做点击事件。第一个盒子的高可以用第二个盒子的高撑开。第二个盒子引用的是图片，该图片的高度需要采用height 的进行限制，放置图片过大超过设计稿的高度。
    - 小叉号的实现，引用矢量字体(在网站中下载对应的字体文件)，使用 i 标签完成，声明字体文件(https://icomoon.io/ 或者 https://www.iconfont.cn 网站生成字体文件)，定位的知识点。
    >使用阿里巴巴的矢量图标库的时候（https://www.iconfont.cn），在网站上选好图标之后，加入购物车；  
    >将所有的图标转换为“项目”, 然后在图标管理 - 图标应用项目中找到这个想， 这里可以获取在线的连接，复制代码或者  
    > 下载到本地进行调用，下载文件保存到fonts文件夹下，然后调用的时候要在url 中正确调用文件所在的路径。可以在.iconfont 类中直接修改字体的样式。
#### 20190629  
5. 快捷导航栏模块
    - 背景通栏、版心放实际信息; (通栏的盒子里面有一个版心)
    - 左列表左浮动，不需要用a 标签
    - 右列表，右浮动，修正li 标签的为none，去除小点，ul去除缝隙，margin 和 padding 置为0
    - 右列表里面的li 也使用浮动，左浮动，去掉一些影响效果的属性
    - 北京前面放置矢量字体作为定位图标，定位坐标(#f10215--京东主色调) 14px, 北京的位置需要让开京东图标的位置，margin-left: 200px;
    - 分割线，竖线使用li 完成，名字叫spacer，宽1px 高10px 边框是字体颜色的，使用margin调整位置， 10px；
    - 下拉菜单，名字dropdown，使用margin留出15px的空间用来放下拉菜单的箭头；
    - 下拉菜单的三角符号，使用矢量字体，使用定位实现（子绝父相），使用浏览器进行实际位置定位；
    - "免费登录" 使用公共样式来修改默认颜色为京东主色调，优先级不够，important来凑。
    - &nbsp来实现空格
    ```
    通栏：hight 30px、 color：E3E4E5,下边框：color：#dddddd 1px solid

    去除li标签的小点 line-style: none
    
    字体颜色：#9D9D9D 12px 字体垂直居中 line-height: 30px 高度与div的高度一致

    a标签去除下划线，text-deceration: none

    移动到a标签时，a标签变色 a:hover: #c81623

    子绝父相：定位时，相对的position位置需要注意一下
    /* 使用padding-right，i使用定位的时候就相对于li的最外层，如果使用margin-right 那么i定位时就相对于除了margin之外的边缘*/

    二维码: 宽60px 高60px 边框 1px solid #ccc，使用调试找到合适的top 和 left的值
    ```
    - 手机京东下面的二维码，使用定位 ？？？三角符号
#### 20190703
6. header部分
    - 总共6个模块，全部使用定位的方式来实现
    - header模块，内部放一个版心，版心内放6个模块，版心内位置如果偏移找到导致偏移的标签，将标签标准化。
    - 模块一 logo，京东狗，最好的效果 div.logo>h1>a
    - box shadow 可以考虑再去了解一下
    ```
        header的 高度 140px;
        logo：宽高 190px 170px 定位，logo的区间都是a标签的范围。a里面的京东两个字不能删掉，为了网站优化，完成搜索优先级；
        box-shadow: 0 -12px 10px rgb(0, 0, 0, 0.2)
    ```
7. 网站优化三大标签
    ##### 站内优化和站外优化
    - 网页title Google(70KB 35个中文) Baidu(56KB 28个中文) 建议：网站名 + 简短网站介绍，越前面的词语权重越高
    - 网站说明 description ,搜索引擎显示的简短说明，不要超过120个汉字;
    - 页面关键字 Keywords ，在搜索引擎搜索关键词的时候可以直接搜索到该网站;
    ```
        <title>XXXXX网站标题</title>
        <meta name="description" content="XXXXX简短说明"/>
        <meta name="Keywords" content="XXXXXX网站包含的关键词">
    ``` 

#### 20190704
8. 搜索部分
    - input、button
    - button的搜索，将鼠标变成小手，cursor：pointer，小圆圈，放大镜， button里面放上i标签 内放搜索的矢量字体
    - 相机部分，精灵图，精灵图采用坐标的方式来选择需要显示的，background-position -30px 0(x y)
    ```
        div 宽高: 550px * 35px  left:320px top: 25px
        input 标签的大小要减去变宽的大小 宽高 498px * 33px 边框，取消蓝色边框 outline：none 文字加上左边距5px
        input默认内容：微单相机 color颜色修改成 #989898
        button 标签 宽50px 去除边框 button(border: 0px) 行内块和行内块之间有缝隙，使用浮动来去除缝隙。
        i 矢量字体 16px
        相机采用绝对定位，父亲search也使用绝对定位，top 10px right 65px 宽高 19px 15px
    ```
9. 热词部分
    - 全部使用a 标签 hotwords top 70px left 320px
10. 购物车
    - top 和 搜索部分一致 宽高 200px 35px 定位靠右定位。
    - font-size 14px 水平垂直居中 text-align：center line-height： 33px
    - 购物车数量，行高16px，字体大小 12px，border-radius：6px （定位 top 5px left 140px）
11. computer部分
    - a标签实现，使用a标签背景用图片就可以了。定位 right 0 bottom 10px
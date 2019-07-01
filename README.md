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
    - 背景通栏、版心放实际信息;
    - 左列表，右列表（分别使用左浮动、右浮动），
    - 字体
    - 背景前面放置矢量字体，定位坐标(#f10215) 14px, margin-left: 200px;
    
    ```
    背景信息：hight 30px、 color：E3E4E5,底边框：color：#dddddd 1px solid

    去除li标签的小点，ul 使用margin 0 padding 0
    
    字体颜色：#9D9D9D 12px 垂直居中

    a标签去除下划线，text-deceration: none

    a:hover: #c81623

    ```
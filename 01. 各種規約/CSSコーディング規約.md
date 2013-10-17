#CSS 编码规范  
---
##CSS代码有效性
######开启浏览器的自动check功能(chrome).推荐使用 w3c css validator 校验其余的代码
##缩进		
######每一行的层级由2个空格缩进,禁止使用Tab
		
##行
- 每个属性必须以分号结尾
- 将选择器和声明隔行。每个选择器和声明都要独立新行

		/* 不推荐 */
		a:focus, a:active {
		  position: relative; top: 1px;
		}

		/* 推荐 */
		h1,
		h2,
		h3 {
		  font-weight: normal;
		  line-height: 1.2;
		}

- 每个规则独立一行.两个规则之间隔行。

		html {
		  background: #fff;
		}
		
		body {
		  margin: auto;
		  width: 50%;
		}
##空格
- 选择器与 { 之前（必须）要有空格
- 属性名的 : 后（必须）要有空格
- 属性名的 : 前（禁止）加空格
 
		.hotel-content {
		  font-weight: bold;
		}
#注释
- 文件注释

		/*!
		 * Bootstrap v3.0.0
		 *
		 * Copyright 2013 Twitter, Inc
		 * Licensed under the Apache License v2.0
		 * http://www.apache.org/licenses/LICENSE-2.0
		 *
		 * Designed and built with all the love in the world by @mdo and @fat.
		 */
- 单行注释

		.hotel-content {
		  font-weight: bold; /* 字体加粗 */
		}

- 组注释

		/* Header */
		#adw-header {}
		
		/* Footer */
		#adw-footer {}
		
		/* Gallery */
		.adw-gallery {}
#命名
- 类和ID都用小写,多个词之间用"-"间隔.命名参考**最佳实践**中的常用名.命名尽可能简短.
#声明
- 类型选择器
>避免使用CSS类型选择器,非必要的情况下不要使用元素标签名和ID或class进行组合.出于性能上的考虑避免使用父辈节点做选择器.为了性能原因,请避免元素选择器和类选择器以及 id 选择器混用(????????????????)
>
>		/* 不推荐 */
>		ul#example {}
>		div.error {}
>		
>		/* 推荐 */
>		#example {}
>		.error {}

- 属性缩写
>写属性值的时候尽量使用缩写.CSS很多属性都支持缩写shorthand （例如 font ） 尽量使用缩写，甚至只设置一个值

>		/* 不推荐 */
>		border-top-style: none;
>		font-family: palatino, georgia, serif;
>		font-size: 100%;
>		line-height: 1.6;
>		padding-bottom: 2em;
>		padding-left: 1em;
>		padding-right: 1em;
>		padding-top: 0;
>		
>		/* 推荐 */
>		border-top: 0;
>		font: 100%/1.6 palatino, georgia, serif;
>		padding: 0 1em 2em;
>		
>		background : [イメージ] [位置] [カラー] ；
>		border : [値] [type] [カラー] ;
>		list-style:[タイプ][位置][イメージ] ;

- 0
>省略0后面的单位,非必要的情况下 0 后面不用加单位。

>		margin: 0;
>		padding: 0;

>省略0开头小数点前面的0。值或长度在-1与1之间的小数，小数前的 0 可以忽略不写

>		font-size: .8em;

- URI
>省略URI外的引号。不要在 url() 里用 ( "" , '' ) 。

>		@import url(//www.google.com/css/go.css);

- 十六进制
>十六进制尽可能使用3个字符。加颜色值时候会用到它，使用3个字符的十六进制更短与简洁。

>		/* 不推荐 */
>		color: #eebbcc;
>		
>		/* 推荐 */
>		color: #ebc;

- 前缀
>选择器前面加上特殊应用标识的前缀（可选）。大型项目中最好在ID或class名字前加上这种标识性前缀（命名空间），使用短破折号链接。使用命名空间可以防止命名冲突，方便维护，比如在搜索和替换操作上。

>		.login-help {} /* login page */
>		#detail-note {} /* detail page */

- Hacks
>避免css hack,考虑使用特定浏览器前缀表示
>
>		.ks-ie6 p {
>		    margin: 1em 0;
>		}

- css属性书写
布局定位属性–>自身属性–>文本属性–>其他属性
按字母的先后顺序来进行css属性的声明(google)

		margin
		padding
		float（包括clear）　
		position（相应的 top,right,bottom,left）　
		display
		visibility
		overflow等； 
		自身属性主要包括:
		width 
		height
		background  
		border; 
		文本属性主要包括：　
		font
		color
		text-align
		text-decoration
		text-indent等；
		其他属性包括: 
		list-style(列表样式)
		vertical-vlign
		cursor
		z-index(层叠顺序) 
		zoom等。

#最佳实践
- 文件必须使用utf-8 编码

		@charset "utf-8";
- 原则上不允许在html标签上写css

- 如果有浏览器属性时 -webkit- -moz- -ms-  -o-顺序.且属性名称要对齐.

		  -webkit-transition: -webkit-transform 0.3s ease-out;
		     -moz-transition: -moz-transform 0.3s ease-out;
		       -o-transition: -o-transform 0.3s ease-out;
		          transition: transform 0.3s ease-out;
- reset.css样式 http://www.cssreset.com/
- 常用名
 
		头：header　　
		内容：content/container　　
		尾：footer　　
		导航：nav　　
		侧栏：sidebar
		栏目：column　　
		页面外围控制整体布局宽度：wrapper　　
		左右中：left right center　　
		登录条：loginbar　　
		标志：logo　　
		广告：banner　　
		页面主体：main　　
		热点：hot　　
		新闻：news
		下载：download　　
		子导航：subnav　　
		菜单：menu　　
		子菜单：submenu　　
		搜索：search　　
		友情链接：friendlink　　
		页脚：footer　　
		版权：copyright　　
		滚动：scroll　　
		内容：content
		标签页：tab
		文章列表：list
		提示信息：msg
		小技巧：tips
		栏目标题：title
		加入：joinus
		指南：guild
		服务：service
		注册：regsiter
		状态态：status
		投票：vote
		合作伙伴：partner
		id的命名
		(1)页面结构
		容器: container
		页头：header
		内容：content/container
		页面主体：main
		页尾：footer
		导航：nav
		侧栏：sidebar
		栏目：column
		页面外围控制整体布局宽度：wrapper
		左右中：left right center
		(2)导航
		导航：nav
		主导航：mainbav
		子导航：subnav
		顶导航：topnav
		边导航：sidebar
		左导航：leftsidebar
		右导航：rightsidebar
		菜单：menu
		子菜单：submenu
		标题: title
		摘要: summary
		(3)功能
		标志：logo
		广告：banner
		登陆：login
		登录条：loginbar
		注册：regsiter
		搜索：search
		功能区：shop
		标题：title
		加入：joinus
		状态：status
		按钮：btn
		滚动：scroll
		标签页：tab
		文章列表：list
		提示信息：msg
		当前的: current
		小技巧：tips
		图标: icon
		注释：note
		指南：guild
		服务：service
		热点：hot
		新闻：news
		下载：download
		投票：vote
		合作伙伴：partner
		友情链接：link
		版权：copyright
		主要的 master.css
		模块 module.css
		基本共用 base.css
		布局，版面 layout.css
		主题 themes.css
		专栏 columns.css
		文字 font.css
		表单 forms.css
		补丁 mend.css
		打印 print.css		
# 第一章 Google Chrome扩展介绍

这一章你将学习Google Chrome 扩展——一种非常有用的方式来增强Google Chrome浏览器功能。首先我们将迅速浏览一下一些流行的Google Chrome应用扩展和一些编码技术。然后在我们介绍了Google Chrome扩展的特性和能力之后，你将学习如何开发你自己的“Helle World”形式的Chrome扩展。最后，你将会学习如何在Google Web Store（前身为Google Chrome Extensions Galleery）发布Chrome扩展。
	
本章假定你已经有了一些使用HTML、CSS和Javascript技术进行简单web页面开的的经验。

### 1.1 Google Chrome 扩展是什么?
Google Chrome扩展是一种用于Google Chrome web浏览器的浏览器扩展。浏览器扩展是一种运行在web 浏览器环境（安全沙箱）中的程序。它们通过结合浏览器现有的特性为浏览器提供新的功能并且使用户可以做很多事。

**注意：**
>在写这本书的时候，Google浏览器扩展只支持桌面版的Google Chrome网页浏览器。

##### 1.1.1 浏览器支持
2010年发布的第四版Google Chrome网页浏览器开始支持浏览器扩展。也可以为Safari、火狐（Mozilla Firefox）和欧朋（Opera）开发扩展。自从Opera转向Chromium的扩展模型（Opera抛弃了自己的Presto引擎转而支持来源于Chromiun项目的webkit引擎，Google Chrome浏览器使用的也是该引擎）后，为Google Chrome浏览器开发的扩展也与Opera浏览器兼容。

开发Safari浏览器扩展与开发Chrome浏览器扩展有着类似的学习曲线，并且二者开发都比较容易，因为开发者不需要学习任何新的技术（只需要用到现有的web技术）。但是开发火狐（Firefox）浏览器扩展却相对困难，因为其使用了一些区别于web技术的开发技术，比如XUL,XPCOM等等（你可以从链接处了解更多有关内容https://en.wikipedia.org/wiki/Add-on_(Mozilla)#Extension_technologies）。 这本书仅仅涉及到在Google Chrome浏览器上开发扩展。

**注意：**
>Chrome web Store是一个在线应用市场，用户可以浏览Chrome应用、扩展和主题。这个应用市场可以帮助用户寻找、购买和安装内容到Chrome浏览器。

### 1.1.2 扩展并不是插件

需要重点注意的是浏览器扩展（Extension）和浏览器插件（Plugin）是不同的。浏览器扩展运行在宿主浏览器的沙箱中，而浏览器插件不是。这里，沙箱可以认为是一个软件容器，它允许执行web技术，访问浏览器的特性，比如标签页、历史记录、弹出菜单等等。

除此之外，扩展通过结合浏览器已经存在的一些特性给浏览器增加新的功能（以Chrome扩展为例，这是通过使用扩展框架提供的API实现的）。然而，插件通过对特殊媒介类型提供浏览器支持来增加浏览器功能。前者的例子可以为，某款扩展可以使用户将所有处于非隐藏模式的标签保存到本地存储，而后者的例子可以是，某款插件允许在浏览器中阅读和渲染PDF文件。

还有一点需要注意的是，开发者可以给浏览器开发另外一种web应用，这种应用被称作Google Chrome Apps。从开发者的视角看，Google Chrome Apps是介于Chrome扩展和Chrome插件的应用。
	
这本书将专注于Google Chrome扩展的开发而不会讨论Google Chrome Apps的开发。但是，需要记住的是开发Chrome扩展和开发Chrome Apps是非常类似的。如果你想知道更多关于Google Chrome Apps开发的内容，你可以访问以下链接：

- https://en.wikipedia.org/wiki/Google_Chrome_Apps
- https://developer.chrome.com/apps/about_apps
- http://stackoverflow.com/questions/tagged/google-chrome-app

### 1.1.3 扩展和插件
要获得你的Chrome浏览器中已经安装的全部扩展，转到标签页chrome://extensions,如图1所示。此页（被称作扩展管理页）是用来管理浏览器的扩展。

![](/assets/1-1.png)

**注意:**
>图1中的这一项并不是Chrome扩展而是Chrome App。Chrome扩展和Chrome App都显示在同一个被称为“扩展管理页”的浏览器页面（chrome://extensions）。除此之外，Chrome App也在其专有的页面（chrome://apps）列出。

考虑该tab页（在该tab页单击右键然后选择Pin Tab选项，如图1-2所示），本书中将经常用到这一操作。

![](/assets/1-2.png)

**注意：**
>沙箱是一项经常用到的技术用来测试或执行未验证的程序（可能包含病毒或其他恶意代码），所以沙箱中运行的程序不会危害主机程序。
	
类似的，要想查看浏览器中已安装的全部插件可转到chrome://plugins（如图1-3所示）。

![](/assets/1-3.png)

一些知名的浏览器插件包括Adobe Flash Player，The Chrome PDF Viewer, the QuickTime Player以及Java插件。

### 1.2 重要的例子
截至2010年2月，已经有约2000款扩展在Chrome Web Store上（http://en.wikipedia.org/wiki/Google_Chrome_Extensions#cite_note-4）。但是，令人惊叹的是，截至2014年9月，Chrome Web Store上已经有30000多个应用扩展！

**注意:**
>“web浏览器”和“浏览器”两个词交互的贯穿于全文，但是他们指代的是同一个东西，即桌面版的网页浏览器。

Google Chrome用于倚赖浏览器扩展来增加工作中的创造性，增强获取网页数据（已可用）的能力并且使之成为他们最喜欢的web浏览器。下面的列表提供了一些来自于Google Web Store非常受欢迎并且免费的Google Chrome浏览器扩展。注意，这些统计数据取自2016年4月。

- Adblock Plus—10,000,000+ 用户
- AddThis: Share & Bookmark—600,000+ 用户
- Awesome Screenshot: Capture & Annotate—900,000+ 用户
- Evernote Web Clipper—4,500,000+ 用户
- Google Dictionary—3,000,000+ 用户
- Google Translate—6,000,000+ 用户
- Hangouts—6,500,000+ 用户
- LastPass: Free Password Manager—4,000,000+ 用户
- Photo Zoom for Facebook—1,500,000+ 用户
- Pin It Button—10,000,000+ 用户



注意，想查看Google Web Store上所有（免费和付费）的Google Chrome浏览器扩展，请访问http://chrome.google.com/webstore/category/extensions

### 1.3 从应用商店添加扩展
从应用商店添加扩展至浏览器非常简单，首先，你需要访问扩展商店（https://chrome.google.com/webstore/category/extensions），一旦你进入商店，你可以选择任何你想要添加的组件。
	
其次，在选择页面，你需要点击Add to Chrome按钮,如图1-4所示。

![](/assets/1-4.png)

最后，点击“添加扩展”按钮进行确认。恭喜你，你已经成功的将该扩展添加至你的Chrome浏览器！

![](/assets/1-5.png)

正如前面提到，你可以转到chrome://extensions去看看添加的扩展。刚刚添加的扩展将会出现在列表中(如图1-6所示)。

![](/assets/1-6.png)

**注意:** 
>类似于chrome-plugins-url（chrome://plugins）和chrome\-extensions\-url（chrome://extensions），有一些其他有用的URL（图1-7）可以用来获得更多的关于你的浏览器的信息。想获得完整的URL列表，可以在浏览器中打开chrome://chrome-urls，如图1-7

![](/assets/1-7.png)

### 1.4 Chrome扩展开发技术
Google Chrome扩展给用户提供了很多功能，同时也可开发者提供了很多便利。开发Google Chrome扩展的技术仅仅是HTML、CSS、Javacript和JSON（通常是必须的）！正因为如此，相较于其他浏览器扩展开发，Google浏览器开发有一个平滑的学习曲线。并且，Google Chrome扩展可以在任何桌面操作系统进行生成，毕竟这些扩展仅仅是一些HTML和Javascript文件的打包。

#### 1.4.1 这些技术是如何使用的？
显而易见，HTML和CSS用于创建扩展的视图，Javascript用于提供应用逻辑以及访问Google Chrome扩展框架提供的API和组件（关于API和组件的知识分别在第二张和第三章深入介绍）。最后，JSON是用来为扩展创建manifest文件，manifest文件向浏览器提供一些关于扩展的信息。

### 1.5 扩展API
Google Chrome扩展运行在浏览器的沙箱中。该沙箱将扩展的代码隔离起来执行。这意味着可能同时有上百个扩展安装在浏览器，但是这些扩展并不会自动意识到其他扩展的存在。这意味着

- 不同的扩展不可能互相建立联系。某个扩展不能自动获取属于另外一个扩展的代码或内存
- 不会有任何命名冲突。Chrome浏览器不会混淆某个扩展中名为Script_A.js脚本和其他扩展中的同名脚本。这一特点同样适用于其他属于扩展的文件，比如HTML、JSON、images等等
- 扩展之间可以以一种确定的和受控的方式建立联系（通信）。扩展框架提供了进行一次连接和长久连接的消息API（第三章将介绍更多这方面内容）

**注意：** 
>除了这里描述的这种沙箱外，Chrome浏览器还提供了另外一种沙箱（注入到web页面运行的脚本）。你将会在第三章看到。
	
Chrome扩展非常有助于增强Chrome浏览器的功能。他们结合Chrome浏览器的特性来提供一些常见的功能，例如，Chome扩展访问标签页和警告API在预定的间隔（比如1天）内打开一个标签页。

Google Chrome浏览器扩展框架提供了许多特殊用途API的扩展，用于提供对Chrome浏览器强大功能的访问。 这些API可以访问Chrome浏览器中几乎所有可用的功能。

**注意：** 
>Google Chrome 扩展框架提供了许多用于特殊目的API。扩展也可以使用web浏览器提供的标准Javascript API。有一些你已经熟悉的核心Javasceript 和DOM API。除此之外，也支持XMLHttpRequest,HTML5（和一些新兴的）API，Webkit API（用于CSS动画、过滤等）以及V8 API（比如JSON）。
>Chrome 浏览器支持的HTML5和其他新兴API包括audio、canvas、geolocation、localstorage、notification以及video。了解更多相关API请访问http://developer.chrome.com/extensions/api_other



###### 使用这些API，你可以在我们的扩展中集成浏览器提供的不同的特性。这些特性列表包括警告、书签、历史、标签、行为、存储、消息通知。搜索等等。你将在第三章学习这些API。

### 1.6 开发你的第一个扩展
你将开发的第一个扩展叫做ShowTime。该扩展将在Google Chrome浏览器工具栏添加一个可点击的按钮（也被称为Browser-Action按钮）。点击这个按钮将会打开一个显示时间和日期的弹出页（如图1-8）

![](/assets/1-8.png)

**注意：**
>manifest.json是扩展中唯一保留文件名的，扩展中的其他文件可以任意命名。

为了开始，你需要建立一个包含以下文件的文件夹：popup.html、popup\_script.js、icon.png、manifest.json。

![](/assets/1-9.png)
	
然后，当你学习发布之后，你将发现刚创建的文件夹被压缩并且上传到Chrome Web Store.

**注意：**	
>当你发布扩展时，相同文件夹将会被打包压缩并且上传（通过Developer Dashboard）到Chrome Web Store.这也在图1-30和1-32中得到了验证。对于你开发的其他扩展也同样适用。
	
正如稍早所述，HTML文件代表着弹出页的视图。Javascript文件将包含应用逻辑（在该例中是显示当前时间和日期）。manifest文件向浏览器提供一些关于扩展的信息。显而易见，浏览器将会用icon.png文件为扩展生成按钮（如图1-10）。

![](/assets/1-10.png)

#### 1.6.1 验证JSON文件
现在是时候用你最喜欢的文本编辑器打开manifest.json文件了。但在你做这件事之前，你需要知道JSON文件中不能有任何注释，既不能有单行注释也不能有多行注释。很多在上传扩展包至Chrome Web Store时遇到的错误都是源于JSON文件中存在注释。这些注释在本地Chrome浏览器中进行测试时是不会被报告的。
	
**注意：**
>为了说明，在代码清单及相关材料中使用了很多注释。

所以，任何时候当你觉得你的manifest文件不在最佳状态时（比如，他可能包含一些错别字或格式错误），你可以放心大胆的使用一些JSON验证器。网上有很多这样的验证器。比如，http://jsonlint.com,http://jsonschemalint.com等等。你可以根据这些验证器的反馈结果打开你的manifest文件进行相应的修改。

#### 1.6.2 创建manifest文件
将下面几个属性添加到空的manifest文件中：manifest\_version,name,version。这些是manifest文件中必须的域。manifest\_version表示manifest文件格式的版本，name表示该扩展的名字。类似的，version是该扩展的版本。
	
manifest\_version是一个大于0的整数值，在写这本书的时候，该属性的有效值是2，表示这是manifest文件格式的第二个版本。version属性是一个由0-4个点分隔符与整数值组成的字符串，每个整数值得范围为0~65536。类似的，name是一个表示扩展名的字符串。你也可以增加一个description属性（字符串值），用来简单的描述该扩展。

**注意：**
>Google Chrome浏览器中的自动更新系统比较（前述）扩展的版本，以确定扩展是否需要更新。 如果发布的扩展名比已安装的扩展名具有更新的版本字符串，则扩展名会自动更新。 在写这本书的时候，扩展更新频率是五个小时。

#### 1.6.3 添加Browser-Action按钮
	
现在需要给Google Chrome工具栏的按钮添加点击相应代码。这种按钮也被称为Broser-Action按钮或者简称Broser-Action。为此，你需要给manifest文件添加另外一个browser\_action属性。browser\_action的属性值是一个对象(即{})，该对象包含default\_title、default\_icon、default\_popup键(string类型)。
	
正如你在代码清单1-1中所看到的，每一个键都对应着string类型的值，键default\_title表示Browser-Action的提示文字，键default\_icon表示作为Browser-Action图标的PNG图片资源的相对路径，类似的，default\_popup表示作为弹出视图的HTML文件的相对路径。

**Listing 1-1.** Chapter1/ShowTime/manifest.json

	{
		"manifest_version" : 2,
		"name" : "ShowTime",
		"description" : "Extension to show the current time and date",
		"version" : "1.2",
		"browser_action" : {
			"default_title" : "ShowTime",
			"default_icon" : "icon.png", //Used as the icon in the Chrome toolbar
			"default_popup" : "popup.html"
		},
		"icons" : {
			"16" : "icon16.png", //Used as the favicon for an extension's pages
			"48" : "icon48.png", //Used on the extension management page
			"128" : "icon128.png" //Used during installation & in the Chrome Web Store
		}
	}
	
现在我们将目光转向其他部分：弹出视图的Javascrip和HTML代码。毫不惊奇的是，创建弹出视图与创建其它普通的静态网页没有什么区别。对于Javascript代码，Chrome扩展框架既提供用于特殊目的的API，也提供所有标准的Javascript API。
	
这意味着，ShowTime扩展中所有的JavaScript代码都可以用标准的JavaScript API，包括Date API(用来获取当前日期及时间)和DOM API(用来获取DOM树)。
	
你可以尝试着写JavaScript代码来获取当前时间和日期，比如说写在head标签（h1,h2等等）里。代码清单1-2和1-3展示了这样的用法。

**Listing 1-2.** Chapter1/ShowTime/popup_script.js

	//region {variables and functions}
	var timeId = "time";
	var dateId = "date";
	var days = ["Sun","Mon","Tue","Wed","Thu","Fri","Sat"];
	var months = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","
	Nov","Dec"];
	var consoleGreeting = "Hello World! - from popup_script.js";
	function setTimeAndDate(timeElement,dateElement) {
		var date = new Date();
		var minutes = (date.getMinutes() < 10 ? '0' : '') + date.getMinutes();
		var time = date.getHours() + ":" + minutes;
		//In "date.getMonth", 0 indicates the first month of the year
		//In "date.getDay", 0 represents Sunday
		var date = days[date.getDay()] + ", " + months[date.getMonth()] + "
		" + date.getDate() + " " + date.getFullYear();
		timeElement.innerHTML = time;
		dateElement.innerHTML = date;
	}
	//end-region
	
在代码清单1-2中需要注意的是Date对象的getMonth方法，该方法返回0-11，分别对应1-12月。并且，Date对象的getDay方法返回0-6，分别对应周日-周六。并且，setTimeAndDate方法接收两个参数，分别表示显示当前时间与日期的DOM元素。

**Listing 1-3.** Chapter1/ShowTime/popup_script.js

	//region {calls}
	console.log(consoleGreeting);
	document.addEventListener("DOMContentLoaded",function(dcle) {
		var timeElement = document.getElementById(timeId);
		var dateElement = document.getElementById(dateId);
		setTimeAndDate(timeElement,dateElement);
	});
	//end-region

代码清单1-3包含剩余的JavaScript代码，setTimeAndDate就是在这里面被调用的。你可以看到，在document加载完成之后再获取DOM是一个好的做法，这也是为什么要在DOMContentLoaded事件里面调用setTimeAndDate方法的原因。
	
你可能会对console.log方法的输出结果产生疑惑，这将会在接下来关于如何调试Chrome扩展的位置进行讲解，但是在这之前，你得先知道如何从浏览器中加载Chrome扩展。这将在下一节“如何加载扩展文件夹”中讨论。

**Listing 1-4.** Chapter1/ ShowTime/popup.html

	<!DOCTYPE html>
	<html>
	<head>
	<!-- The following tag is not obeyed -->
	<title>ShowTime (Custom)</title>
	<!--
	<script>
	// Inline scripts are not allowed
	alert('Hello World');
	</script>
	-->
	<!-- Referring scripts is allowed -->
	<script src="popup_script.js"></script>
	<style>
	body {
		padding:0px;
		margin:0px;
		width:300px;
		height:200px;
	}
	
看一看代码清单1-4和1-5，它们包含着HTML代码。这里有一点特别需要注意的是：弹出页中内联JavaScript是不允许的。但是JavaScript是可以从外部引入的，就像代码清单中一样。Src必须指向JavaScript文件的相对路径（相对于扩展文件夹）。另外，你也可以将应用逻辑分散在多个JavaScript文件里面，但是每一个都必须单独引入。Style标签里面的CSS代码也可以提取到外部的CSS文件然后像这样<link type=’text/css’ rel=’stylesheet’ href=’some\_file.css’>引入进来。

**Listing 1-5.** Chapter1/ ShowTime/popup.html

	h1,h2 {
		display:table-row;
		vertical-align:middle;
		text-align:center;
	}
	h2 {
		background-color:#777;
	}
	.unselectable {
		-webkit-user-select:none;
		cursor:default;
	}
	</style>
	</head>
	<body>
	<div class="unselectable">
	<h1 class="empty"></h1>
	<h1 id="time"></h1>
	<h2 id="date"></h2>
	</div>
	</body>
	</html>

### 1.7 加载扩展文件夹

Chorme浏览器提供了一种非常简单快捷的方式来加载扩展文件夹(用作测试目的)。注意到浏览器不需要额外的文件，它只期望获得一个包含着HTML、JavaScript以及JSON的文件夹，下面的步骤证明了如何加载扩展文件夹：

1. 转到扩展管理页面。回顾一下该页面所在的URL chrome://extensions（图1-1）
2. 开启页面上的“开发者模式”选项。（图1-11）
3. 这将会在页面增加额外的一块区域，该区域有加载、打包和更新扩展按钮。（如图1-11）
4. 点击“加载未打包扩展”按钮，一个文件夹选择弹出将会弹出来让你选择扩展所在的文件夹（如图1-12）
5. 选择你创建的ShowTime文件夹，点击“确定”继续。就是这么一回事！你已经最终将你的扩展加载到浏览器里了（如图1-13和1-14）。正如前面所讨论的，如果你的manifest文件的格式有错误，页面上将会显示“Manifest is not valid JSON”字样，它会要求你改正错误后重新加载。

![](/assets/1-11.png)
![](/assets/1-12.png)

**注意:** 
>你也可以通过选择扩展管理页面的“在隐身模式下启用”让你的扩展运行在隐身模式下。

![](/assets/1-13.png)

一旦扩展被成功加载，你也可以在扩展管理页面对它进行配置，如图1-13所示。最后，为了看到弹出视图，你需要点击浏览器右上角的Browser-Action按钮（ShowTime扩展对应的那个）。当你鼠标悬停在按钮上时，你也会看到提示文字（回顾一下提示文字是通过manifest文件的default_title键设置的）。接下来你将会知道如何调试Chrome扩展。

### 1.8 调试扩展
在这一节，你将会学习如何调试Chrome扩展，毫不惊奇，调试Chrome扩展和调试普通的额网页没什么不同。你最好的调试朋友——你一定已经猜到了——Chrome DevTools。
	
这里不会对Chrome DevTools讨论太多，因为谷歌开发社区已经提供了很多优秀的资源让新手以及经验丰富的开发者熟悉在Chrome浏览器上调试Web应用程序。下面这个URL可以带你去那里：https://developers.google.com/web/tools/chrome-devtools

### 1.8.1 检查弹出视图
第一种你可以进行的调试是检查弹出视图，要进行该调试，你只需要在弹出视图上点击鼠标右键（当点击Browser-Action按钮使得弹出视图显示之后），然后选择你需要检查的元素，如图1-14所示。

![](/assets/1-14.png)

**注意：** 
>你也可以采用另外一种方式检查弹出视图：当你右键点击扩展图标的时候选择“检查弹出视图”选项。

如图1-15所示。包含着你所检查的弹出视图元素的Chrome DevTools窗口将会打开，你可以在这个面板里编辑样式以及DOM元素，以一种交互的方式看看哪种设计更符合需求。

![](/assets/1-15.png)

### 1.8.2 来源与资源面板
在调试过程中可用的其他面板包括“来源”面板和“资源”面板。 使用Sources面板，您可以通过在脚本中设置断点来调试JavaScript代码。 为了做到这一点，首先需要选择需要调试的特定脚本（见图1-16）。 接下来，单击要设置断点的行的行号。 最后（保持在DevTools窗口内），重新加载DevTools窗口来激活断点。

![](/assets/1-16.png)

**注意：** 
>您还可以通过单击每行的行号，在“来源”面板中将多个断点添加到脚本中。

使用“资源”面板，可以检查加载的其他资源，例如本地存储和会话存储。 然而，我们不会将这些类型的存储用于本书，因为Google Chrome扩展框架为扩展提供了更好的存储API。 它允许跨多个设备同步存储的数据，这不是由localStorage和sessionStorage API提供的。

您仍然可以尝试在您开发的扩展中使用它们。 通过“资源”面板检查存储非常简单。 如图1-17所示，您只需选择需要检查的存储类型的资源项即可。

![](/assets/1-17.png)

### 1.8.3 控制台面板
控制台面板是Chrome DevTools窗口中的典型（JavaScript）REPL。 使用它，不仅可以记录诊断信息，还可以使用它作为shell与页面上的JavaScript进行交互。 控制台面板如图1-18所示

![](/assets/1-18.png)

在扩展开发环境中，这意味着您可以使用控制台面板来记录脚本中的数据。 您可以记录数据的方式是使用console.log方法。 这个方法需要输出一个JavaScript对象的变量列表。

**注意：** 
>使用console.clear方法清除控制台日志。

除此之外，使用控制台面板，您还可以与Google Chrome扩展框架提供的各种API进行交互。 回想一下，所有这些都是在扩展开发的背景下进行的，所以这些API只能用于属于扩展的（脚本或页面）。 例如，在您开发的ShowTime扩展中，您还可以添加以下几行代码来记录是否可以使用隐身模式访问该扩展。 实际上，您可以直接在控制台面板中执行此代码（同时检查弹出窗口）。

	chrome.extension.isAllowedIncognitoAccess(function(isAllowed) {
		console.log(isAllowed);
	});

当您了解了更多的用于构建扩展的其他组件时，您会发现控制台面板是帮助您快速调试扩展的不可或缺的工具。 在接下来创建新扩展的章节中将会有更多的展示。 现在，我们来探讨如何通过Chrome网上应用店分发扩展程序。

### 1.9 发布到商店
一旦创建了令人惊叹的扩展程序，您很快就有将其分发到Chrome网上应用店的需求。 当用户在Chrome浏览器搜索此类产品时，这将帮助您向多个用户推销您的应用、扩展程序或主题。 Chrome网上应用店允许您通过其开发人员信息中心分发扩展程序。 在撰写本文时，开发人员面板位于以下URL：https：//chrome.google.com/webstore/developer/dashboard。 在本节中，我们将一步步将ShowTime扩展程序上传到Chrome网上应用店。

**（一）** 输入以下网址，即开发者信息中心：https：//chrome.google.com/webstore/developer/dashboard。 如果您未登录Google帐户，系统会要求您登录，如图1-19所示。 成功登录后，您将被重定向到图1-20所示的开发人员面板。

![](/assets/1-19.png)
![](/assets/1-20.png)

**注意：**
>Google帐户ID不一定必须是Gmail ID，但通常情况下是。

**（二）** 进入开发者信息中心后，您需要查看有关开发者帐户的基本信息。 在撰写本文时，可以在支付开发者注册费之前查看这些信息。

**注意：**
>验证您的帐户和发布项目需要缴纳5.00美元的一次性开发者注册费。


**（三）** 接下来，您需要支付开发者注册费。 这是一次性费用，用于验证您的帐户和发布项目。 在撰写本文时，这个数字是5.00美元。 点击立即支付此费用按钮启动付款流程。

**（四）** 如图1-21和图1-22所示，您需要添加付款方式。 如果您已经有与Google帐户关联的付款方式，则可以继续下一步。

![](/assets/1-21.png)
![](/assets/1-22.png)

**（五）** 检查您所购买的（见图1-23），然后点击购买进行下一步。

![](/assets/1-23.png)

**（六）** 最后，您可以点击Start Now按钮启动支付，如图1-24所示。

![](/assets/1-24.png)

**（七）** 在成功完成付款流程后，Google电子钱包将会显示一个窗口，感谢您的购买。 如图1-25所示，单击完成返回到开发人员面板。

![](/assets/1-25.png)

**注意：**
>汇率波动，银行手续费和适用的税金可能会改变您的最终金额。

**（八）** 在开发人员面板中，单击添加新项按钮（请参见图1-26）将新扩展加载到面板。

![](/assets/1-26.png)

**（九）** 在这里，您需要上传扩展文件夹的压缩包。 为此，您必须单击图1-27中的“选择文件”按钮。 但在你做之前，你需要对ShowTime扩展增加一些东西。

![](/assets/1-27.png)

**（十）** 如清单1-1所示，您需要将icons属性添加到清单文件中。 该属性接受以下键值对的对象值（即{}）：

1. "16" : "icon16.png":这个16px图标被用作扩展页面的图标
2. "48" : "icon48.png": 这个48px图标在扩展管理页面上使用（如图1-28所示）
3. "128" : "icon128.png": 这个128像素的图标在安装过程中和Chrome网上应用店使用

![](/assets/1-28.png)

**（十一）** 现在，您已将图标属性添加到manifest.json中，您还需要添加相应的图像。 您可以创建自己的或使用第1章的 Exercise
Files文件夹中提供的（请参见图1-29）。 注意，键16,48和128表示要使用的PNG图像资源的（相对）路径。

![](/assets/1-29.png)

**（十二）** 最后，您可以创建此扩展文件夹的压缩包，并继续步骤9。

**（十三）** 选择压缩包后，点击上传按钮（见图1-30）。

![](/assets/1-30.png)

**（十四）** 成功上传压缩包后，面板将重新加载（请参见图1-31）以反映做出的更改

![](/assets/1-31.png)

**（十五）** 如果您的manifest文件格式不正确（或者还有其他相关的缺陷，例如缺少图像资源等），则会在此阶段显示错误，如图1-32所示

![](/assets/1-32.png)

**（十六）** 然后，您的扩展程序进入编辑模式（见图1-33）。 你可以按你的方式自由填写。

![](/assets/1-33.png)

**（十七）** 最后，您可以发布您所做的更改，也可以在商店上发布扩展，也可以选择保存草稿。 如果您想再试一次，您也可以放弃当前的草稿。 现在，通过单击保存草稿并返回面板，如图1-34所示。

![](/assets/1-34.png)

当您返回面板时，您将在“您的清单”部分下找到您的扩展程序的草稿，如图1-35所示。 随着您对扩展的进一步了解，您可以改进和更新此草稿。 最后，当您准备好使用此扩展程序时，可以更新步骤16中讨论的字段并发布扩展。

![](/assets/1-35.png)

### 1.10 总结

本章从浏览器扩展的基本定义开始介绍，内容包括它们是什么以及不是什么。然后，您学会了通过“扩展管理”页面列出安装在Chrome浏览器中的扩展程序。
接下来，讨论了一些值得注意的扩展，之后您还学会了在Chrome浏览器上安装扩展。还介绍了创建Chrome扩展的技术，并将其与其他浏览器上使用的技术进行了比较。

最后，您创建了第一个名为ShowTime的扩展，并学会了在Chrome浏览器中加载它。不仅如此，您还学会了调试您的扩展程序并将其上传到Chrome网上应用店。在第2章中，您将详细了解Chrome扩展的开发及其体系结构。但在继续之前，请确保在您创建的ShowTime扩展程序中进行尝试，以更好地感受开发过程。这将使您更加熟悉下一章中使用的示例扩展，在那一章您将了解扩展的体系结构。
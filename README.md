# jquery.lazyload 使用介绍

Lazy Load 这个 jQuery 插件，是用来缓冲加载图片的插件。如果一篇文章很长有很多图片的话，下载图片就需要很多时间。而这款插件，会检测你的滚动情况，只有你要看到那个图片的时候，它才会从后台请求下载图片，然后显示出来。使用这个插件，可以在需要显示图片的时候，才下载图片，所以可以减少服务器的压力，避免不必要的资源下载。

http://www.appelsiini.net/projects/lazyload

##如何使用

第一种：加载相关文件。

很明显，你要加载jquery和这个插件。你可以使用以下代码，加载这几个文件：

	<script src="jquery.js" type="text/javascript"></script>
	<script src="jquery.lazyload.js" type="text/javascript"></script>

第二种

支持fis的component的组件生态直接

	require('jquery-lazyload');

##第二步：定义图片结构。

按照官方的建议，定义你的img结构：

	<img src="img/grey.gif" data-original="img/example.jpg" width="640" heigh="480" class="lazy">

##第三步：触发这个插件，生效。

激活以下，你就可以在目标中使用了。

	$(".lazy").lazyload();




#方法

##提前加载

默认的情况是，当你滚动到图片位置的时候，插件开始加载。这样，用户可能首先看到的是一个空白图像，然后再缓慢出现。如果你想在用户滚动之前，提前加载这个图像，你可以配置一下参数。

	$("img.lazy").lazyload({ threshold : 200 });
threshold 这个参数，就是用来提前加载的。上面这个语句的意思是，当距离图片还有200像素的时候，就开始加载图片。

##自定义触发事件

默认的触发事件，是滚动，当你滚动的时候，就会检查然后加载。你可以使用event属性，设置你自己的加载事件，之后你可以自定义触发这个事件的条件，然后去加载图像。

$(".lazy").lazyload({ event : "click" });

##自定义显示效果

默认的图片实现效果，就是没有效果，下载完成之后，直接显示出来。这样的用户体验并不好，你可以设置 effect 属性，来控制显示图片的效果。例如

$(".lazy").lazyload({ effect : "fadeIn" });


##把图像插入某个容器

大家如果使用智能手机的话，经常去应用网站下载应用，他们通常使用一个横着的容器，放一些手机截图。使用 container 属性，能很轻松在容器中实现缓冲加载。首先，我们需要用css定义这个容器，然后用这个插件进行加载。效果： vertical

	#container { height: 600px; overflow: scroll; }
	$(".lazy").lazyload({         
	     container: $("#container")
	});


##加载不可见图像

有部分图像是不可见的，我们对其加上类似 display：none 等属性的图像。默认的情况下，这个插件是会加载隐藏的不可见图像。如果我们需要用它不加载不可见图像，我们需要将 skip_invisible 设置为 true

$(".lazy").lazyload({ skip_invisible : true });


##加载图片不顺序排列

当图片不顺序排列,滚动页面的时候, Lazy Load 会循环为加载的图片. 在循环中检测图片是否在可视区域内. 默认情况下在找到第一张不在可见区域的图片时停止循环. 图片被认为是流式分布的, 图片在页面中的次序和 HTML 代码中次序相同. 但是在一些布局中, 这样的假设是不成立的. 不过你可以通过 failurelimit 选项来控制加载行为.

	$("img").lazyload({    
		failurelimit : 10    
	});   
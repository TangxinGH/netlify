illustrator 导出svg，用的是同一字体 ，导出到网页，不一样。

原来是原本css文件中中加了serif;line-height: 1.8;等。加上就可以了

我的加font-family没有用。

因此直接写svg标签在html里，而不是img 引入方式。解决字体问题。

后来发现，字体颜色不对。fill="#233300" 来修改颜色。

默认bold加粗

 

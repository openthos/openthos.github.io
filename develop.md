#适配 Android N 多窗口特性的 5 个要诀

如果你看了 [What’s New in Android N](http://v.youku.com/v_show/id_XMTQ5NjgzNDcyNA==.html) 这个视频，你会无意中发现了[多窗口支持](http://developer.android.com/preview/features/multi-window.html?utm_campaign=adp_series_prepareformultiwindow_032316&utm_source=medium&utm_medium=blog)。

使用多窗口分屏功能，能够并排地同时看到两个应用。你可能非常兴奋，想知道这是如何做到的，于是立刻去查阅文档，看看是什么新 API 实现了这一独特功能。

结果却发现并没有出现很多新的 API 。只有少量用于定制是否完全支持多窗口的 XML 属性以及少量用于检查当前是否处于多窗口模式的 Activity 方法。那这个魔法到底打是哪来的？__其实魔法一直都在那__。

所谓的魔法就是 Android 的[资源系统](http://developer.android.com/guide/topics/resources/overview.html?utm_campaign=adp_series_prepareformultiwindow_032316&utm_source=medium&utm_medium=blog)。
资源系统中最强大的部分之一是[提供替代资源](http://developer.android.com/guide/topics/resources/providing-resources.html?utm_campaign=adp_series_prepareformultiwindow_032316&utm_source=medium&utm_medium=blog#AlternativeResources)(alternate resources )的能力——基于不同条件改变大小、
布局、绘制、菜单等等。

__多窗口就是利用了这个资源系统 – 基于窗口大小来调整配置__。除了屏幕大小，最小宽度(即宽度或高度的最小值)和朝向(orientation)也会在调整窗口大小时更新。

这引出了我们第一个要诀。

####要诀1：使用正确的上下文



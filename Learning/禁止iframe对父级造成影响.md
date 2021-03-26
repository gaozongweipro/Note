# 禁止iframe对父级造成影响
给iframe添加sandbox属性  

> allow-same-origin:   允许iframe内容被是为与包含文档有相同对来源

> allow-top-navigation 允许iframe内容从包含文档导航（加载）内容

> allow-forms 允许表单提交  

> allow-scripts 允许脚本执行
 
> allow-popups 允许弹出窗口

> allow-popups-to-escape-sandbox 允许弹出沙箱窗口

> allow-modals 允许模态窗口

> allow-orientation-lock 允许锁定父窗口屏幕方向

> all-pointer-lock 允许使用指针锁API

> allow-presentation 允许控制session

> allow-top-navigation-by-user-activation 允许潜入的浏览上下文在经过用户允许后导航（加载）内容到顶级的浏览上下文

> allow-storage-access-by-user-activation 允许潜入的浏览上下文通过Storage Access API使用父级浏览器上下文的存储功能

> "" 允许上述所有规则，默认

*通过这个限制iframe对父级的影响，解决在swiper组件中使用iframe时，水平方向上的动画效果会受到iframe加载的影响而错位的问题*

```
    // 使用例子
    <template v-if="item[defaultOpt.list.type]==='report'">
      <iframe
        ref="iframe"
        :src="url.reportUrl+item[defaultOpt.list.resource] + '?from=dataexporler' + getReportParams"
        sandbox="allow-forms allow-scripts allow-same-origin allow-popups allow-popups-to-escape-sandbox"
        allowTransparency="true"
        frameborder="0"
        style="width:100%;height:100%;"
      />
    </template>

```
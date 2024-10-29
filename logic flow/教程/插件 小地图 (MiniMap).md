小地图 (MiniMap)
=============

table td:first-of-type { word-break: normal; }

LogicFlow 的画布小地图是一个缩略图视图，帮助用户快速导航和定位大型或复杂图表的不同区域。

本文是 2.0 版本最新语法，2.0 版本以前请移步[旧版](https://docs.logic-flow.cn/docs/#/zh/guide/extension/component-minimap)。

[](#演示)演示
---------

LogicFlow Extension - MiniMap

显示小地图

0-start0-end1-start1-end2-start2-end3-start3-end4-start4-end5-start5-end6-start6-end7-start7-end8-start8-end9-start9-end10-start10-end11-start11-end12-start12-end13-start13-end14-start14-end15-start15-end16-start16-end17-start17-end18-start18-end19-start19-end20-start20-end21-start21-end22-start22-end23-start23-end24-start24-end25-start25-end26-start26-end27-start27-end28-start28-end29-start29-end30-start30-end31-start31-end32-start32-end33-start33-end34-start34-end35-start35-end36-start36-end37-start37-end38-start38-end39-start39-end40-start40-end41-start41-end42-start42-end43-start43-end44-start44-end45-start45-end46-start46-end47-start47-end48-start48-end49-start49-end50-start50-end51-start51-end52-start52-end53-start53-end54-start54-end55-start55-end56-start56-end57-start57-end58-start58-end59-start59-end60-start60-end61-start61-end62-start62-end63-start63-end64-start64-end65-start65-end66-start66-end67-start67-end68-start68-end69-start69-end70-start70-end71-start71-end72-start72-end73-start73-end74-start74-end75-start75-end76-start76-end77-start77-end78-start78-end79-start79-end80-start80-end81-start81-end82-start82-end83-start83-end84-start84-end85-start85-end86-start86-end87-start87-end88-start88-end89-start89-end90-start90-end91-start91-end92-start92-end93-start93-end94-start94-end95-start95-end96-start96-end97-start97-end98-start98-end99-start99-end100-start100-end101-start101-end102-start102-end103-start103-end104-start104-end105-start105-end106-start106-end107-start107-end108-start108-end109-start109-end110-start110-end111-start111-end112-start112-end113-start113-end114-start114-end115-start115-end116-start116-end117-start117-end118-start118-end119-start119-end120-start120-end121-start121-end122-start122-end123-start123-end124-start124-end125-start125-end126-start126-end127-start127-end128-start128-end129-start129-end130-start130-end131-start131-end132-start132-end133-start133-end134-start134-end135-start135-end136-start136-end137-start137-end138-start138-end139-start139-end140-start140-end141-start141-end142-start142-end143-start143-end144-start144-end145-start145-end146-start146-end147-start147-end148-start148-end149-start149-end150-start150-end151-start151-end152-start152-end153-start153-end154-start154-end155-start155-end156-start156-end157-start157-end158-start158-end159-start159-end160-start160-end161-start161-end162-start162-end163-start163-end164-start164-end165-start165-end166-start166-end167-start167-end168-start168-end169-start169-end170-start170-end171-start171-end172-start172-end173-start173-end174-start174-end175-start175-end176-start176-end177-start177-end178-start178-end179-start179-end180-start180-end181-start181-end182-start182-end183-start183-end184-start184-end185-start185-end186-start186-end187-start187-end188-start188-end189-start189-end190-start190-end191-start191-end192-start192-end193-start193-end194-start194-end195-start195-end196-start196-end197-start197-end198-start198-end199-start199-end

缩小

放大

适应

上一步

下一步

[](/~demos/docs-tutorial-extension-minimap-demo-react-portal)

[](#使用)使用
---------

### [](#1-注册)1\. 注册

两种注册方式，全局注册和局部注册，区别是全局注册每一个 `lf` 实例都可以使用。

import LogicFlow from "@logicflow/core";

import { MiniMap } from "@logicflow/extension";

// 全局注册

LogicFlow.use(MiniMap);

// 局部注册

const lf \= new LogicFlow({

  ...config,

  plugins: \[MiniMap\]

});

### [](#2-配置)2\. 配置

在初始化 `lf` 实例时可以通过 `pluginsOptions` 自定义配置 mini-map 的能力。

const miniMapOptions: MiniMap.MiniMapOption \= {

  ...options

}

const lf \= new LogicFlow({

  ...config,

  plugins: \[MiniMap\],

  pluginsOptions: {

    miniMap: miniMapOptions,

  },

});

`miniMapOptions` 配置如下：

属性名

类型

默认值

必填

描述

width

number

150

\-

小地图中画布的宽度

height

number

220

\-

小地图中画布的高度

showEdge

boolean

false

\-

在小地图的画布中是否渲染边

headerTitle

string

导航

\-

小地图标题栏的文本内容，默认不显示

isShowHeader

boolean

false

\-

是否显示小地图的标题栏

isShowCloseIcon

boolean

false

\-

是否显示关闭按钮

leftPosition

number

\-

\-

小地图与画布左边界的左边距，优先级高于`rightPosition`

rightPosition

number

0

\-

小地图与画布右边界的右边距，优先级低于`leftPosition`

topPosition

number

\-

\-

小地图与画布上边界的上边距，优先级高于`bottomPosition`

bottomPosition

number

0

\-

小地图与画布下边界的下边距，优先级低于`topPosition`

[](#api)API
-----------

### [](#show)show

引入 mini-map 后默认不展示，需要手动开启显示。

lf.extension.miniMap.show(left?: number, top?: number): void

`show()` 支持传入样式属性 left 和 top 的值，用来确定 mini-map 在画布中相对于左上角的位置，不传默认显示在画布右下角。

只提供 left 和 top 这两个值是因为可以与`lf.getPointByClient` API 配合使用，如果想实现更加灵活的样式，可以直接通过类名设置样式。

*   `lf-mini-map` - mini-map 根元素
*   `lf-mini-map-header` - mini-map 头部元素
*   `lf-mini-map-graph` - mini-map 画布元素
*   `lf-mini-map-close` - mini-map 关闭图标元素

> `MiniMap.show()`必须在`lf.render()`后调用。

### [](#hide)hide

隐藏 mini-map。

lf.extension.miniMap.hide(): void

### [](#reset)reset

重置 mini-map 的缩放和平移，本质是重置画布的缩放和平移。

lf.extension.miniMap.reset(): void

内部实现：

lf.resetTranslate()

lf.resetZoom()

### [](#updateposition)updatePosition

更新小地图在画布中的位置。

lf.extension.miniMap.updatePosition(MiniMapPosition): void

`MiniMapPosition` 参数如下：

export type AbsolutePosition \= Partial<

  Record<'left' | 'right' | 'top' | 'bottom', number\>

\>

export type MiniMapPosition \=

  | 'left-top' // 表示迷你地图位于容器的左上角

  | 'right-top' // 表示迷你地图位于容器的右上角

  | 'left-bottom' // 表示迷你地图位于容器的右上角

  | 'right-bottom' // 表示迷你地图位于容器的右下角。

  | AbsolutePosition // 自定义小地图在画布上的位置

### [](#setshowedge)setShowEdge

设置小地图的画布中是否显示边。

lf.extension.miniMap.setShowEdge(showEdge: boolean): void

`showEdge`: `true` 显示，`false` 隐藏。

[](#事件)事件
---------

mini-map 事件。

事件名

说明

事件对象

miniMap:close

小地图隐藏

{}

上一篇

控制面板 (Control)

下一篇

框选 (SelectionSelect)优化
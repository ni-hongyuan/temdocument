LogicFlow
=========

table td:first-of-type { word-break: normal; }

[](#实例)实例
---------

流程图上所有的节点实例操作以及事件，行为监听都在 `LogicFlow` 实例上进行。

`LogicFlow`配置项: [constructor](/api/detail/constructor)

[](#实例方法)实例方法
-------------

### [](#graph-相关)Graph 相关

选项

描述

[setTheme](/api/theme)

设置主题。

[focusOn](/api/detail#focuson)

定位到画布视口中心。

[resize](/api/detail#resize)

调整画布宽高, 如果`width` 或者`height`不传会自动计算画布宽高。

[toFront](/api/detail#tofront)

将某个元素放置到顶部。

[getPointByClient](/api/detail#getpointbyclient)

获取事件位置相对于画布左上角的坐标。

[getGraphData](/api/detail#getgraphdata)

获取流程绘图数据。

[getGraphRawData](/api/detail#getgraphrawdata)

获取流程绘图原始数据， 与 `getGraphData` 区别是该方法获取的数据不会受到 `adapter` 影响。

[clearData](/api/detail#cleardata)

清空画布。

[renderRawData](/api/detail#renderrawdata)

渲染图原始数据，在使用`adapter`后，还想渲染 logicflow 格式的数据。

[render](/api/detail#render)

渲染图数据。

### [](#node-相关)Node 相关

选项

描述

[addNode](/api/detail#addnode)

在图上添加节点。

[deleteNode](/api/detail#deletenode)

删除图上的节点, 如果这个节点上有连接线，则同时删除线。

[cloneNode](/api/detail#clonenode)

克隆节点。

[changeNodeId](/api/detail#changenodeid)

修改节点的`id`， 如果不传新的`id`，会内部自动创建一个。

[changeNodeType](/api/detail#changenodetype)

修改节点类型。

[getNodeModelById](/api/detail#getnodemodelbyid)

获取节点的`model`。

[getNodeDataById](/api/detail#getnodedatabyid)

获取节点的`model`数据。

[getNodeIncomingEdge](/api/detail#getnodeincomingedge)

获取所有以此节点为终点的边。

[getNodeOutgoingEdge](/api/detail#getnodeoutgoingedge)

获取所有以此节点为起点的边。

[getNodeIncomingNode](/api/detail#getnodeincomingnode)

获取节点所有的上一级节点。

[getNodeOutgoingNode](/api/detail#getnodeoutgoingnode)

获取节点所有的下一级节点。

### [](#edge-相关)Edge 相关

选项

描述

[setDefaultEdgeType](/api/detail#setdefaultedgetype)

设置边的默认类型, 也就是设置当节点直接由用户手动连接的边类型。

[addEdge](/api/detail#addedge)

创建连接两个节点的边。

[getEdgeDataById](/api/detail#getedgedatabyid)

通过`id`获取边的数据。

[getEdgeModelById](/api/detail#getedgemodelbyid)

基于边 `id` 获取边的`model`。

[getEdgeModels](/api/detail#getedgemodels)

获取满足条件边的`model`。

[changeEdgeId](/api/detail#changeedgeid)

修改边的 `id`， 如果不传新的 `id`，会内部自动创建一个。

[changeEdgeType](/api/detail#changeedgetype)

切换边的类型。

[deleteEdge](/api/detail#deleteedge)

基于边`id`删除边。

[deleteEdgeByNodeId](/api/detail#deleteedgebynodeid)

删除与指定节点相连的边, 基于边起点和终点。

[getNodeEdges](/api/detail#getnodeedges)

获取节点连接的所有边的`model`。

### [](#register-相关)Register 相关

选项

描述

[register](/api/detail#register)

注册自定义节点、边。

[batchRegister](/api/detail#batchregister)

批量注册。

### [](#element-相关)Element 相关

选项

描述

[addElements](/api/detail#addelements)

批量添加节点和边。

[selectElementById](/api/detail#selectelementbyid)

将图形选中。

[getSelectElements](/api/detail#getselectelements)

获取选中的所有元素。

[clearSelectElements](/api/detail#clearselectelements)

取消所有元素的选中状态。

[getModelById](/api/detail#getmodelbyid)

基于节点或边 `id` 获取其 `model`。

[getDataById](/api/detail#getdatabyid)

基于节点或边 `id` 获取其 `data`。

[deleteElement](/api/detail#deleteelement)

删除元素。

[setElementZIndex](/api/detail#setelementzindex)

设置元素的 `zIndex`。

[getAreaElement](/api/detail#getareaelement)

获取指定区域内的所有元素(此区域必须是 DOM 层)。

[setProperties](/api/detail#setproperties)

设置节点或者边的自定义属性。

[getProperties](/api/detail#getproperties)

获取节点或者边的自定义属性。

[deleteProperty](/api/detail#deleteproperty)

删除节点属性。

### [](#text-相关)Text 相关

选项

描述

[editText](/api/detail#edittext)

显示节点、连线文本编辑框, 进入编辑状态，同[graphModel.editText](/graphModel#edittext)。

[updateText](/api/detail#updatetext)

更新节点或者边的文案。

[updateEditConfig](/api/detail#updateeditconfig)

更新流程编辑基本配置。

[getEditConfig](/api/detail#geteditconfig)

获取流程编辑基本配置。

### [](#history-相关)History 相关

选项

描述

[undo](/api/detail#undo)

历史记录操作-返回上一步。

[redo](/api/detail#redo)

历史记录操作-恢复下一步。

### [](#transform-相关)Transform 相关

选项

描述

[zoom](/api/detail#zoom)

放大缩小画布。

[resetZoom](/api/detail#resetzoom)

重置图形的缩放比例为默认，默认是 1。

[setZoomMiniSize](/api/detail#setzoomminisize)

设置图形缩小时，能缩放到的最小倍数。参数一般为 0-1 之间，默认 0.2。

[setZoomMaxSize](/api/detail#setzoommaxsize)

设置图形放大时，能放大到的最大倍数，默认 16。

[getTransform](/api/detail#gettransform)

获取当前画布的缩放值与偏移值。

[translate](/api/detail#translate)

平移图。

[resetTranslate](/api/detail#resettranslate)

还原图形为初始位置。

[translateCenter](/api/detail#translatecenter)

图形画布居中显示。

[fitView](/api/detail#fitview)

将整个流程图缩小到画布能全部显示。

[openEdgeAnimation](/api/detail#openedgeanimation)

开启边的动画。

[closeEdgeAnimation](/api/detail#closeedgeanimation)

关闭边的动画。

### [](#事件系统-相关)事件系统 相关

选项

描述

[on](/api/detail#on)

图的监听事件，更多事件请查看[事件](/api/event-center)。

[off](/api/detail#off)

删除事件监听。

[once](/api/detail#once)

事件监听一次。

[emit](/api/detail#emit)

触发事件。

下一篇

初始化选项
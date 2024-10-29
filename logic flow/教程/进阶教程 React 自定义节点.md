React 自定义节点
===========

#### 我们带来了新特性，本节内容主要介绍

*   如何使用 React 组件来注册节点内容
*   properties 更新后如何同步更新节点内容

[](#渲染-react-组件为节点内容)渲染 React 组件为节点内容
-------------------------------------

我们虽然提供了通过继承 HTMLNode 自定义节点的能力，但从用户反馈来看，这种方式并不够直观且有可能因为销毁时机不对而出现性能问题。

因此我们提供了一个独立的包 `@logicflow/react-node-registry`，以一种更直观的方式来自定义节点，即通过 React 组件来注册节点。 它既可以直接使用系统中已引入的丰富的组件库，也可以使用 React 快捷的开发方式来自定义节点内容。

import { register, ReactNodeProps } from '@logicflow/react-node-registry'

// 自定义 React 组件

const NodeComponent: FC<ReactNodeProps\> \= ({ node }) \=> {

  const data \= node.getData()

  if (!data.properties) data.properties \= {}

  return (

    <div className\="react-algo-node"\>

      <img src\={require('@/assets/didi.png')} alt\="滴滴出行" />

      <span\>{data.properties.name as string}</span\>

    </div\>

  )

}

// 初始化 LogicFlow 实例

const lf \= new LogicFlow({

  // ...options

})

// 注册自定义节点

register({

  type: 'custom-react-node',

  component: NodeComponent,

}, lf)

// 渲染自定义节点

const node \= lf.addNode({

  id: 'react-node-1',

  type: 'custom-react-node',

  x: 80,

  y: 80,

  properties: {

    name: '今日出行',

    width: 120,

    height: 28,

  },

})

console.log('node --->>>', node)

React 自定义节点

![滴滴出行](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAYAAACqaXHeAAAAAXNSR0IArs4c6QAAA7lJREFUeF7tm0Fu1DAUhp0ijYQEZQ0n6L7saQ+ARPcUlmiOwIp2xRFGLKHsi8QBCHu6picoawoS0kht4HfHIePYsf3e80ySTlajUWL7//z7PdtxCrWC69fs+d612tpDVYWqnjSq1P8ppUrzX6WKr+b3g+mHo9zNK3JUAMEot1LFm3/ijEhSVZUqjvFgLhiiACBcQnQHqRIOkYQhAmAFwltM4AwJECwA6xBuk+CCIAO4nB1+4Y5vUlBwPMSBkAxg0esQ37urUNX+/enHOqPENDAJwM/Zi6NCVYjsvb1S3RANYAjiG3OJ6AAZBWBI4lMhBAEMUXwKhE4AQxYfC8ELoM/RPjUCd2UHL4DL2WGVWlGf79+enji1Ov8cg/UdnVFuT0/27f9bAEYqXut2DYUWgLFZ3+rxlguWAIy59w0I2wVLAEbe+4bBkgtqALeh910uqAGkLm/vPNpZeda7ujiXqrN2QRNAUt6/+/S1WjWE+dknNf92KgLBxAINgGL/DYCBOwBb8ZgYaQdQov/QHQDdmB4XFPvj4TEAQBy41QCwfSYOAJH66uK7SKS2C5nsHjjLvfpxTsoOGkBq/jct8A0ByVTVAvD4QE12n7UgYH7w5/NbCvRyA2DjAOLOz0iGgMIQSJoCjywGaACkd3wjcYB8EGRE5GAUzwCdDmAin5LWA4A6FcZSGD3iupCTBdfudRX3Xr0XrY81E0RLfA3KMRnyOQ7t+P3uZdA9rhs0AM4boK4FEbVRPiU+2JyYowFQl8N4rmsYcBoWOwXGfRy36eXwAgApFYaWxZzGNSH4ep9rfxyy0gA4w6DLBdweQtlYAfr2HjmAzUkSNoCQC0xPpja2K+iZMjlxxrwsJW+L2+M0docIIHCZPQOTLk0vmzV/aMc5FajV3va2OGcYmMK7xiopT3keYorHEd76DJH9aowcDENZQQqARHZpnhVYAiDhAgiNGb8UINyeR532MTrX63GWC4wwaQgS4tE2+6RIC4CUC6RAwPLzs1ORtYXrEKXziAx1j6DL1nCEjhMPd4LvFCVFmzb5TpCu7ZCUneZyrB6bHZJ0SIo7O6QEuJzPkI7JoUHUvYKcYlLLDh2e3hyVjSE6RCeEet7oDjrA3DgkCLHioS0awFBiQor4ZAB9zw7ZP5lpxoueDQnnOeCY+JY0BOwCewChLFR1nPqhVFMHC8AaAyRbeHIWiLHTwhH4OJr1vXBHXWLCswCwY8RNlGV/ZqdFoyyO1X1QRYZAyB1wxn/icZ/Pb6nrModgu61/ATUXmCtru/wpAAAAAElFTkSuQmCC)今日出行 3

#1677FF

Show Tooltip

[](/~demos/docs-tutorial-advanced-react-demo-react-basic)

[](#更新节点)更新节点
-------------

跟 `HTMLNode` 一样，当用户通过 `setProperties` 或 `setProperty` 等更新节点 properties 时，我们会自动更新节点内容。

const node1 \= lf.addNode({

  id: 'react-node-1',

  type: 'custom-react-node',

  x: 80,

  y: 80,

  properties: {

    name: '今日出行',

    width: 120,

    height: 28,

  },

})

const update \= () \=> {

  node1.setProperty('name', \`今日出行 ${(this.count += 1)}\`)

  this.timer \= setTimeout(update, 1000)

}

update()

// 记得在 componentWillUnmount 中清除定时器

if (this.timer) {

  clearTimeout(this.timer)

}

[](#portal-方式)Portal 方式
-----------------------

上面的 React 组件渲染方式有一个缺点，因为内部是通过以下方式将组件渲染到节点的 DOM 中。

import { createRoot, Root } from 'react-dom/client'

const root \= createRoot(container)

root.render(elem)

可以发现，React 组件已经不处于正常的渲染文档树中。所以它内部无法获取外部 Context 内容。如果有这种应用场景，可以使用 `Portal` 模式来渲染 React 组件。

React Portal Demo

切换到暗色

![滴滴出行](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAYAAACqaXHeAAAAAXNSR0IArs4c6QAAA7lJREFUeF7tm0Fu1DAUhp0ijYQEZQ0n6L7saQ+ARPcUlmiOwIp2xRFGLKHsi8QBCHu6picoawoS0kht4HfHIePYsf3e80ySTlajUWL7//z7PdtxCrWC69fs+d612tpDVYWqnjSq1P8ppUrzX6WKr+b3g+mHo9zNK3JUAMEot1LFm3/ijEhSVZUqjvFgLhiiACBcQnQHqRIOkYQhAmAFwltM4AwJECwA6xBuk+CCIAO4nB1+4Y5vUlBwPMSBkAxg0esQ37urUNX+/enHOqPENDAJwM/Zi6NCVYjsvb1S3RANYAjiG3OJ6AAZBWBI4lMhBAEMUXwKhE4AQxYfC8ELoM/RPjUCd2UHL4DL2WGVWlGf79+enji1Ov8cg/UdnVFuT0/27f9bAEYqXut2DYUWgLFZ3+rxlguWAIy59w0I2wVLAEbe+4bBkgtqALeh910uqAGkLm/vPNpZeda7ujiXqrN2QRNAUt6/+/S1WjWE+dknNf92KgLBxAINgGL/DYCBOwBb8ZgYaQdQov/QHQDdmB4XFPvj4TEAQBy41QCwfSYOAJH66uK7SKS2C5nsHjjLvfpxTsoOGkBq/jct8A0ByVTVAvD4QE12n7UgYH7w5/NbCvRyA2DjAOLOz0iGgMIQSJoCjywGaACkd3wjcYB8EGRE5GAUzwCdDmAin5LWA4A6FcZSGD3iupCTBdfudRX3Xr0XrY81E0RLfA3KMRnyOQ7t+P3uZdA9rhs0AM4boK4FEbVRPiU+2JyYowFQl8N4rmsYcBoWOwXGfRy36eXwAgApFYaWxZzGNSH4ep9rfxyy0gA4w6DLBdweQtlYAfr2HjmAzUkSNoCQC0xPpja2K+iZMjlxxrwsJW+L2+M0docIIHCZPQOTLk0vmzV/aMc5FajV3va2OGcYmMK7xiopT3keYorHEd76DJH9aowcDENZQQqARHZpnhVYAiDhAgiNGb8UINyeR532MTrX63GWC4wwaQgS4tE2+6RIC4CUC6RAwPLzs1ORtYXrEKXziAx1j6DL1nCEjhMPd4LvFCVFmzb5TpCu7ZCUneZyrB6bHZJ0SIo7O6QEuJzPkI7JoUHUvYKcYlLLDh2e3hyVjSE6RCeEet7oDjrA3DgkCLHioS0awFBiQor4ZAB9zw7ZP5lpxoueDQnnOeCY+JY0BOwCewChLFR1nPqhVFMHC8AaAyRbeHIWiLHTwhH4OJr1vXBHXWLCswCwY8RNlGV/ZqdFoyyO1X1QRYZAyB1wxn/icZ/Pb6nrModgu61/ATUXmCtru/wpAAAAAElFTkSuQmCC)今日出行 3

[](/~demos/docs-tutorial-advanced-react-demo-react-portal)

上一篇

图编辑配置项

下一篇

Vue 自定义节点新特性
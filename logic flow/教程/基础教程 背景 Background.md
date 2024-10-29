背景 Background
=============

### [](#提供可以修改画布背景的方法包括背景颜色或背景图片背景层位于画布的最底层)提供可以修改画布背景的方法，包括背景颜色或背景图片，背景层位于画布的最底层。 info

创建画布时，通过 `background` 选项来设置画布的背景层样式，支持透传任何样式属性到背景层。默认值为 `false` 表示没有背景。

const lf \= new LogicFlow({

  background: false | BackgroundConfig,

})

type BackgroundConfig \= {

  backgroundImage?: string,

  backgroundColor?: string,

  backgroundRepeat?: string,

  backgroundPosition?: string,

  backgroundSize?: string,

  backgroundOpacity?: number,

  filter?: string, // 滤镜

  \[key: any\]: any,

};

[](#配置项)配置项
-----------

### [](#设置背景颜色)设置背景颜色

const lf \= new LogicFlow({

  // ...

  background: {

    backgroundImage: "url(../asserts/img/grid.svg)",

    backgroundRepeat: "repeat",

  },

});

[](#示例)示例
---------

[去 CodeSandbox 查看示例](https://codesandbox.io/embed/infallible-goldberg-mrwgz?fontsize=14&hidenavigation=1&theme=dark&view=preview)

上一篇

网格 Grid

下一篇

事件 Event
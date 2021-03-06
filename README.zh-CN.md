<h1 align="center"> SVG-Skeleton </h1>

<p align="center">
    <a href="https://opensource.org/licenses/MIT">
        <img alt="Licence" src="https://img.shields.io/badge/license-MIT-green.svg" />
    </a>
    <a href="https://www.npmjs.org/package/svg-skeleton">
        <img alt="NPM" src="https://img.shields.io/badge/npm-v0.0.4-brightgreen.svg" />
    </a>
    <a href="">
        <img alt="Size" src="https://img.shields.io/badge/size-2kb-blue.svg" />
    </a>
</p>

## 为什么使用

骨骼屏我们都并不陌生，而骨骼屏的最大的存在意义是 由于页面渲染出内容的时间较长，而使用它在页面上占位，让用户感知白屏的时间减少。

若骨骼屏依赖 React / Vue 等核心框架的时候，必然先需要解析核心库，才到骨骼屏的渲染，这样无疑不是最佳选择。

**SVG-Skeleton** 正是我们一直所期望的方案的实现。

通过 SVG 元素去描述去骨骼图的占位元素，支持 JSX 让编写 SVG 无差别化，复用 SVG 片段，类组件化模式。

## 安装

```sh
npm i svg-skeleton --save
```

或者

```html
<script src="https://cdn.jsdelivr.net/npm/svg-skeleton/dist/svg-skeleton.min.js"></script>
```

## 使用

### JSX 代码

```js
import SVGSkeleton from 'svg-skeleton';

const { h, render } = SVGSkeleton;

// 内置 #shining 动画
const Item = (
    <svg width="750" height="191">
        <circle cx="95" cy="102" r="63" fill="#edeff0" mask="url(#shining)" />
        <rect width="160" height="35" x="190" y="45" fill="#edeff0" mask="url(#shining)" />
        <rect width="400" height="35" x="190" y="90" fill="#edeff0" mask="url(#shining)" />
        <line x1="0" y1="190" x2="750" y2="190" stroke="#edeff0"></line>
    </svg>
);

const Page = ( ( ) => {
    let List = [ ];

    for ( let i = 0; i < 6; i++ ) {
        List.push( ( <Item y={ i == 0 ? 0 : i * 191 } /> ) );
    }

    return (
        <svg width="750" height="1334" fill="#fafafa">
            { List }
        </svg>
    );
} )( );

render( Page,  document.body );
```

### 输出

<p align="center">
    <img src="./README/1.gif" width="250px">
</p>

## Diff

为了尽量骨骼屏幕的元素的位置跟设计稿一样，你需要 Diff 这个功能。

### 代码

```js
const { diff } = SVGSkeleton;

render( diff( Page, require('./list.png') ),  document.body );
```

### 输出

<p align="center">
    <img src="./README/2.gif" width="250px">
</p>


## 依赖 [JSX & h](https://www.npmjs.com/package/babel-plugin-transform-react-jsx)

设置类似于

```json
{
    "plugins": [
        [ "transform-react-jsx", { "pragma": "h" } ]
    ]
}
```

## 许可

[MIT](./LICENSE)

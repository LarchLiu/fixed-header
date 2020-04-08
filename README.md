[![Image from Gyazo](https://i.gyazo.com/9ba5b1c59cdd50467c042e691c421d3e.gif)](https://gyazo.com/9ba5b1c59cdd50467c042e691c421d3e)  

[![Edit fixed-header demo](https://codesandbox.io/static/img/play-codesandbox.svg?style=flat-square)](https://codesandbox.io/s/fixedheader-n6w0d)

## Introduction

 * 支持传递组件的内部 class name 来 fixed 内部组件
 * 同一页面如有多个 FixedHeader 请为每个组件传递 idName, 因为是通过 id 找到具体的组件, 如果 id 相同多个组件无法区分
 * 单个 FixedHeader 可不用传递 idName, 只需在页面定义默认的名为 fixed-header 的样式, 不考虑层级关系可以定义 /deep/.fixed-header
 * 不用默认样式名称需传入自定义的 styleClassName
 
## Usage

#### 页面只有一个 FixedHeader

```
<template>
  <div class="fixed">
      <fixed-header>
        <div>fixed header</div>
      </fixed-header>
  </div>
</template>

<script>
import FixedHeader from '@/components/FixedHeader'

export default {
  components: {
    FixedHeader
  }
}
</script>

<style>
.fixed {
    /deep/.fixed-header {
      position: fixed;
      left: 0;
      top: 0;
      width: 100%;
    }
}
</style>
```

#### 页面如有多个 FixedHeader  
其中 child-class-name 传入的是已封装的 el-tabs 的头部 class name，通过此 name 固定 tab header

```
<template>
    <fixed-header id-name="top" style-class-name="top-fixed-header">
      <span>top fixed header</span>
    </fixed-header>
    <fixed-header child-class-name="el-tabs__header">
      <el-tabs type="border-card">
        <el-tab-pane label="商品介绍">
          <div>商品介绍</div>
          <img src="http://dummyimage.com/1000x1000/02adea/FFF&text=Hello">
          <img src="http://dummyimage.com/1000x1000/3538b2/FFF&text=Mock.js">
        </el-tab-pane>
        <el-tab-pane label="规格参数">
          规格参数
        </el-tab-pane>
        <el-tab-pane label="商品评价">
          商品评价
        </el-tab-pane>
      </el-tabs>
    </fixed-header>
</template>

<script>
import FixedHeader from '@/components/FixedHeader'

export default {
  components: {
    FixedHeader
  }
}
</script>

<style>
.fixed {
    /deep/.fixed-header {
      position: fixed;
      left: 0;
      top: 0;
      width: 100%;
    }
    /deep/.top-fixed-header {
        position:fixed;
        background: red;
        color: white;
        top:0;
        width: 100%;
        z-index:999;
      }
}
</style>
```
#### props  
##### idName  
* 需要 fixed 组件 id 名称，用于定位组件  
* default: element  
##### styleClassName
* 组件 fixed 时的样式名称  
* default: fixed-header
##### childClassName
* 需要 fixed 组件中的子组件 class name, 用于定位到此子组件
* default: null


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

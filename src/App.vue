<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <fixed-header id-name="top" style-class-name="top-fixed-header">
      <span>top fixed header</span>
    </fixed-header>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
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
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import FixedHeader from '@/components/FixedHeader'

export default {
  name: 'app',
  components: {
    HelloWorld,
    FixedHeader
  }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  min-height: 2000px;
  /deep/.fixed-header {
    position:fixed;
    top:22px;
    width: 100%;
    z-index:999;
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

---
title: some problems of vue-amap
date: 2021-05-06 10:00:26
tags:
---

## vue-amap的一些注意点

>**'AMap' is not defined.**

在.eslintrc.js中添加如下配置：
```js
  globals: {
    AMap: true
  }
```

>**实时监听zoom参数变化**

利用ref获取地图实例，调取getZoom方法
```js
  <el-amap
    ref="map"
    vid="amapDemo"
    :amap-manager="amapManager"
    :zoom="zoom"
    :center="center"
    :plugin="plugin"
    :events="events"
    class="amap-demo"
  />

  data() {
    return {
      events: {
        zoomchange: (e) => {
          // 更新当前地图实例zoom
          this.zoom = this.$refs['map'].$$getInstance().getZoom()
        },
      }
    }
  }
```
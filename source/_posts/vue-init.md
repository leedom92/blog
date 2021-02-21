---
title: Vue.js
date: 2021-02-13 23:21:44
---
## start

```html
<div id="app">
  <h1>{{ name }}</h1>
</div>
```

```js
const vm = new Vue({
  el: '#app',
  data: {
    name: 'leedom'
  }
})
```
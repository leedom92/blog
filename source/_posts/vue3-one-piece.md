---
title: 'Vue 3.0 "one piece"'
date: 2021-02-13 23:21:44
---

![vue3.0](vue3-one-piece.png)

## example

```html
<div id="app">
  <h1>{{ name }}</h1>
</div>
```

```js
const app = {
  data() {
    return {
      name: 'leedom'
    }
  }
}

Vue.createApp(app).mount('#app')
```

<p class='codepen' data-height='300' data-theme-id='dark' data-preview='true' data-default-tab='js,result' data-lazy='true' data-editable='true' data-slug-hash='MWbEJjj'>
  <span>See the Pen <a href='https://codepen.io/leedom92/pen/MWbEJjj'>
  MWbEJjj</a> by leedom92 (<a href='https://codepen.io/leedom92'>@leedom92</a>)
  on <a href='https://codepen.io'>CodePen</a>.</span>
</p>
<script async src='https://static.codepen.io/assets/embed/ei.js'></script>

## vue 2.0

```html
<div id="app">
  <h1>{{ name }}</h1>
</div>
```


```js
const app = new Vue({
  el: '#app',
  data: {
    name: 'leedom'
  }
})
```

<p class='codepen' data-height='300' data-theme-id='dark' data-preview='true' data-default-tab='js,result' data-editable='true' data-slug-hash='mdOBmwp'>
  <span>See the Pen <a href='https://codepen.io/leedom92/pen/mdOBmwp'>
  mdOBmwp</a> by leedom92 (<a href='https://codepen.io/leedom92'>@leedom92</a>)
  on <a href='https://codepen.io'>CodePen</a>.</span>
</p>

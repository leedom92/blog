---
title: 'Vue 3.0 "one piece"'
date: 2021-02-13 23:21:44
---
## start

![vue3.0](vue3-one-piece.png)

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
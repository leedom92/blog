---
title: 'Vue.js: a (re)introduction'
tags: []
excerpt: |2-

      
        
        
          <p style="text-align:center"><img src="/images/logo.png" style="width:200px;display:inline-block"></p>

  <p><a href="http://vuejs.org" target
        
      
      
date: 2015-10-25 23:02:14
---

![](/images/logo.png)
<!-- more -->
![](/images/logo.png)

[Vue.js](http://vuejs.org) is a library for building web interfaces. Together with some other tools you can also call it a “framework”, although it’s more like a set of optional tools that work together really well. Now, if you’ve never heard of or used Vue before, you are probably thinking: great, yet another JavaScript framework! I get it. Turns out Vue isn’t particularly new — I first started working on its prototype almost two years ago, and the first public release was in [February 2014](http://blog.evanyou.me/2014/02/11/first-week-of-launching-an-oss-project/). Over the time it has been evolving, and today [many are using it in production](https://github.com/vuejs/awesome-vue#projects-using-vuejs).

So, what exactly does Vue offer? What makes it different? Why in the world would you want to learn about it when there are already Angular, Ember and React? This post attempts to shed some light on these question by taking you through a brief tour of Vue.js concepts, and I hope you will have your own answers after reading it.

## [](#Reactivity "Reactivity")Reactivity

> Keeping the state and the view in sync is hard. Or is it?

Let’s start with the most basic task: displaying data. Suppose we have a simple object:

var object = {  
 message: 'Hello world!'  
}  

And a template:

<div id\="example"\>  
 {{ message }}  
</div\>  

And here’s how we bind the data and the template together with Vue:

new Vue({  
 el: '#example',  
 data: object  
})  

Looks like we just rendered a template. What should we do to update the view when the object changes? The answer is… _nothing_. Vue has converted the object and made it “reactive”. When you set `object.message` to something else, the rendered HTML updates automatically. More importantly, there’s no need to worry about calling `$apply` in a timeout, or calling `setState()`, or listening to store events, or creating framework-proprietary observables like `ko.observable()` or `Ember.Object.create()`… it just works.

Vue also provides seamless computed properties:

var example = new Vue({  
 data: {  
 a: 1  
 },  
 computed: {  
 b: function () {  
 return this.a + 1  
 }  
 }  
})  
  
// both a & b are proxied on the created instance.  
example.a // -> 1  
example.b // -> 2  
example.a++  
example.b // -> 3  

The computed property `b` tracks `a` as a dependency, and is automatically kept in sync. No need to declare the dependencies yourself, because you shouldn’t have to.

In addition, POJO-based reactivity makes it trivially easy to integrate with any type of data-source or state management solutions. For example, here’s an integration that enables Vue.js components to bind to RxJS Observables with [less than 30 lines of code](https://github.com/vuejs/vue-rx/blob/master/vue-rx.js#L22-L51).

## [](#Components "Components")Components

> Ok the data binding is neat for small demos. What about big apps?

When it comes to structuring complex interfaces, Vue takes an approach that is very similar to React: it’s components all the way down. Let’s make our example a reusable component:

var Example = Vue.extend({  
 template: '<div>{{ message }}</div>',  
 data: function () {  
 return {  
 message: 'Hello Vue.js!'  
 }  
 }  
})  
  
// register it with the tag <example>  
Vue.component('example', Example)  

Now we can use the component in other templates simply as a custom element:

<example\></example\>  

Components can contain other components, and they form a tree that represents your UI. To make them actually composable, Vue components can also:

*   Define how it expects to receive data from its parent using `props`;
*   Emit custom events to trigger actions in parent scope;
*   Compose parent injected content with its own template using `<slot>`.

We are not going to go into the details here, but if you are interested, checkout more in the [official guide](http://vuejs.org/guide/components.html).

## [](#Modularity "Modularity")Modularity

> It’s 2015 and we shouldn’t put everything in the global scope!

Let’s use a module bundler ([Webpack](http://webpack.github.io/) or [Browserify](http://browserify.org/)) and use ES2015. Each component can just be in its own module. Since Vue will automatically convert option objects into component constructors, we can simply export an object:

// ComponentA.js  
export default {  
 template: '<div>{{ message }}</div>',  
 data () {  
 return {  
 message: 'Hello Vue.js!'  
 }  
 }  
}  

// App.js  
import ComponentA from './ComponentA'  
  
export default {  
 // use another component, in this scope only.  
 // ComponentA maps to the tag <component-a>  
 components: { ComponentA },  
 template: \`  
 <div>  
 <p>Now I'm using another component.</p>  
 <component-a></component-a>  
 </div>  
 \`  
}  

Pretty nice, huh? Wouldn’t it be even better if we can encapsulate a component’s template, styles and JavaScript logic in the same file, and getting proper syntax highlighting for each? With tools like Webpack + [vue-loader](https://github.com/vuejs/vue-loader) or Browserify + [vueify](https://github.com/vuejs/vueify), you can:

<!-- MyComponent.vue -->  
  
<!-- css -->  
<style\>  
.message {  
 color: red;  
}  
</style\>  
  
<!-- template -->  
<template\>  
 <div class\="message"\>{{ message }}</div\>  
</template\>  
  
<!-- js -->  
<script\>  
export default {  
 props: \['message'\],  
 created() {  
 console.log('MyComponent created!')  
 }  
}  
</script\>  

> Wait a minute, did we just re-invent Web Components? But your CSS is still global!

Well, sort of, except:

*   You _can_ have style encapsulation. Just add a `scoped` attribute to the `<style>` tag. And it does _not_ leak down to nested child components.
    
*   Each Vue component is compiled into a JavaScript module, and doesn’t need any polyfill to work all the way down to IE9. You can also wrap it inside a real Custom Element if you want.
    
*   ES2015 is supported by default in `<script>` tags.
    
*   You can use _any pre-processor_ you want in each language block.
    
*   When using Webpack + vue-loader, you also get to leverage Webpack’s full power for static asset handling, because the template and styles are piped through `html-loader` and `css-loader` that can handle asset URLs as module dependencies.
    

So yeah, if you want you can have components that look like this:

![vue component](/images/vue-component.png)

Oh, and did I mention Vue components are hot-reloadable?

![vue hot reload](/images/vue-hot.gif)

## [](#Animations "Animations")Animations

> Can I make fancy stuff with it?

Vue ships with a built-in [transition system](http://vuejs.org/guide/transitions.html) that is very simple to use. There are many [award-winning interactive sites](https://github.com/vuejs/awesome-vue#interactive-experiences) built with it.

Vue’s reactivity system also makes it trivially simple to do efficient state-based tweening, which turns out to be quite a hassle in frameworks that use dirty-checking or Virtual DOM diffing. When you tween a piece of state at 60 frames per second, Vue accurately knows which bindings are affected, so it efficiently updates the affected bindings, and the rest of the app is unaffected. In both dirty checking and Virtual DOM diffing, changing a piece of state means the whole affected sub-tree (be it scopes or components) needs to be digested/re-rendered. Although it is usually “fast enough” in small demos, it most likely won’t be when you are triggering changes 60 times per second in a large app. Even if it manages to be fast enough, it will be draining device battery for all the wasted cycles. Check out [this talk](https://www.youtube.com/watch?v=xtqUJVqpKNo) to get a sense how much effort is needed to animate things efficiently in React. Vue apps are just optimized by default in these scenarios.

An example of state-based tweening with Vue:

See the Pen [Vue.js elastic header component](http://codepen.io/yyx990803/pen/XmZNOG/) by Evan You ([@yyx990803](http://codepen.io/yyx990803)) on [CodePen](http://codepen.io).

## [](#Routing "Routing")Routing

> So I want to build an app, but where’s the router?

Like React, Vue itself doesn’t come with routing. But there’s the [vue-router](https://github.com/vuejs/vue-router) package to help you out. It supports mapping nested routes to nested components and offers fine-grained transition control. Here’s a simple example:

import Vue from 'vue'  
import VueRouter from 'vue-router'  
import App from './app.vue'  
import ViewA from './view-a.vue'  
import ViewB from './view-b.vue'  
  
Vue.use(VueRouter)  
  
const router = new VueRouter()  
  
router.map({  
 '/a': { component: ViewA },  
 '/b': { component: ViewB }  
})  
  
router.start(App, '#app')  

The template for `app.vue`:

<div\>  
 <h1\>This is the layout that won't change</h1\>  
 <router-view\><!-- matched component renders here --></router-view\>  
</div\>  

For an actual example, check out this [HackerNews Clone](https://github.com/vuejs/vue-hackernews) built with Vue.js, vue-router, Webpack and vue-loader.

## [](#Stability "Stability")Stability

> A personal project? Seriously?

Yes, this is a personal project. So if you are looking for an enterprise backed dev team, Vue is probably not the one. But I’d rather look at the numbers. Vue has maintained [100% test coverage](https://codecov.io/github/vuejs/vue?branch=master) on every single commit since the 0.11 rewrite, and that will continue. GitHub issues are closed within [an average of 13 hours](http://issuestats.com/github/vuejs/vue), and there has been 1400+ of them. As of this writing, there are literally _zero_ open and reproducible bugs.

Vue just recently [reached 1.0](http://vuejs.org/2015/10/26/1.0.0-release/), which means it’s production ready. The API is going to stay stable. For the 0.12 -> 1.0 upgrade, there is a migration build which ships with all the new features while remaining fully backwards compatible. The deprecation warnings will essentially guide users through the upgrade process. And that is going to be the case for any future breaking releases as well.

Well, I hope I’ve convinced at least some of you to take a deeper look at Vue. I believe it provides a valuable alternative to what’s out there, and I’d love to see you build some great stuff with it. Feel free to check out the [docs](http://vuejs.org), or come hangout in the [forum](http://forum.vuejs.org/) and [gitter channel](https://gitter.im/vuejs/vue). Oh, and even if you don’t want to use Vue, you should [follow me on Twitter](https://twitter.com/youyuxi).
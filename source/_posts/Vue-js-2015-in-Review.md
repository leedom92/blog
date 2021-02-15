---
title: 'Vue.js: 2015 in Review'
tags: []
excerpt: |2-

      
        
        
          <p style="text-align:center"><img src="/images/trend.png" style="width:600px;display:inline-block"></p>

  <p>The year of 2015 has been a pret
        
      
      
date: 2015-12-20 23:12:12
---

![](/images/trend.png)

The year of 2015 has been a pret
<!-- more -->
![](/images/trend.png)

The year of 2015 has been a pretty crazy ride for Vue.js. The project has grown way beyond my expectations, so I’d like to take a look back and put things in perspective.

## [](#Stats "Stats")Stats

### [](#General "General")General

*   NPM downloads: 382,184 ytd, ~52k/month current
*   GitHub Stars: 11,357 current

Unfortunately Bower and CDNs do not offer download statistics - there should be at least equal if not more usage from these sources, since a considerable portion of Vue.js users use it for non-SPA purposes and pull it directly from a CDN.

The GitHub star count saw a whopping 7.6k+ growth since February. In comparison, the project collected a total of ~3.6k stars in its first year (Feb 2014 - Feb 2015).

### [](#Repo-Activity "Repo Activity")Repo Activity

*   Releases: 54 ytd (from 0.11.5 to 1.0.12, including alpha/beta/rc releases)
*   Commits: 1,023 ytd
*   Issues Closed: 1,014 ytd
*   Pull Requests Merged: 69 ytd from 43 contributors

### [](#Vuejs-org "Vuejs.org")Vuejs.org

*   Page views: 3,761,728 ytd
*   Unique visitors: 363,365 ytd
*   30 Day Active Users: 76,090 current

## [](#Highlights "Highlights")Highlights

### [](#Adoption-in-the-Laravel-Community "Adoption in the Laravel Community")Adoption in the Laravel Community

It all started with this…

> Current React learning status: overwhelmed. Learning [@vuejs](https://twitter.com/vuejs) because it looks easy and has pretty website. 👍
> 
> — Taylor Otwell (@taylorotwell) [April 20, 2015](https://twitter.com/taylorotwell/status/590281695581982720)

Taylor Otwell, the author of [Laravel](https://laravel.com/), picked up Vue.js instead of React as he was searching for a new front-end library. Soon afterwards Jeffrey Way created a screen cast series on [Laracasts](https://laracasts.com) which popularized Vue.js in the Laravel community. Today some of the most active Vue.js users are from the Laravel community and there are really cool open source projects like [Koel](http://koel.phanan.net/) built with the two technologies combined.

### [](#Shipping-1-0 "Shipping 1.0")Shipping 1.0

1.0 was some really hard work: careful considerations had to be made on what to deprecate, and there was lengthy, heated discussion around the template syntax overhaul. But in the end I believe we ended up with something most of us are happy with. With the goal of providing a painless migration path, I’m also quite proud that I was able to provide 1.0 builds that are fully backwards-compatible with deprecation warnings.

The release of 1.0 was a great boost to the project’s adoption. The release post stayed on HackerNews front page for quite a while, gathering more than 300 upvotes. The GitHub star count surged, and Vue has stayed in the GitHub JavaScript trending list almost every day since then. In Google trends, the curve for Vue.js is showing strong growth and [recently surpassed Backbone and Ember](https://www.google.com/trends/explore#q=vuejs%20%2B%20vue.js%2C%20backbone.js%20%2B%20backbonejs%2C%20emberjs%20%2B%20ember.js&cmpt=q&tz=Etc%2FGMT%2B5).

### [](#Growing-Ecosystem "Growing Ecosystem")Growing Ecosystem

In addition to Vue.js core, we now also have a whole suite of official libraries/tools that help with building larger applications:

*   [vue-loader](https://github.com/vuejs/vue-loader) and [vueify](https://github.com/vuejs/vueify) for component-based build workflow;
*   [vue-router](https://github.com/vuejs/vue-router) for routing in SPAs;
*   [vue-devtools](https://github.com/vuejs/vue-devtools) for live inspection and debugging;
*   [vuex](https://github.com/vuejs/vuex) for explicit state management in large scale applications.

Of course, there are also many [awesome community contributed projects](https://github.com/vuejs/awesome-vue#libraries--plugins) - a big shoutout to the community for sharing what you’ve built!

### [](#Podcasts "Podcasts!")Podcasts!

I did a bunch of podcasts this year, mostly talking about Vue.js. These podcasts touch upon some pretty in-depth topics about Vue.js, so if you are interested about the nitty-gritty details, they are probably worth listening to!

*   [JavaScript Jabber](https://devchat.tv/js-jabber/187-jsj-vue-js-with-evan-you)
*   [The Changelog](https://changelog.com/184/)
*   [Fullstack Radio](http://www.fullstackradio.com/30)
*   [Teahour.fm (Chinese)](http://teahour.fm/2015/08/16/vuejs-creator-evan-you.html)

## [](#Reflections "Reflections")Reflections

### [](#The-Progressive-Framework "The Progressive Framework")The Progressive Framework

People often ask me how Vue.js compares to other frameworks. There are of course a lot of technical details, but I’ve talked enough about them in the podcasts. The more fundamental question is why does Vue.js exist and what purpose does it serve. To be honest, I often asked that question myself - especially when almost everyone is talking about React in 2015. But despite React’s dominance, there are still a lot of people liking and using Vue.js - in fact, more and more of them. Every few days I’d get a Twitter mention about how Vue.js has made someone’s life easier. This makes me believe that Vue.js is filling some right gaps in the world of web development.

The web is extremely versatile and the web developer population is immensely diverse. From static content sites to complex enterprise applications, people use and build for the web in drastically different ways. Every solution comes with tradeoffs for the specific type of problems it is trying to solve. For example, when trying to manage the inherent complexity of large scale applications, fully-opinionated frameworks often introduce non-trivial accidental complexity in terms of architecture, concepts and tooling, which renders them cumbersome for simple scenarios. On the other hand, when stitching together micro-libraries to handle large scale apps, the amount of research, wiring and plumbing can be intimidating.

What I believe Vue.js got right, is that it starts with solving the most essential problem of web development - declaratively mapping state to the DOM - in the least intrusive way possible. If that is all you need, then the complexity level can be grasped within minutes. When the app becomes bigger, you will probably start using components, but it doesn’t necessarily have to be an SPA. For real SPAs, you can introduce `vue-router`, but it’s still up to you whether to use a module build system. Finally, for a full-blown, modularized SPA, it’s still up to you whether you want to manage your state with Vuex…

This is what I call a “Progressive Framework”: the key is that _we can scale up the framework’s complexity incrementally, only when the project’s inherent complexity demands it._ And when you do scale up, you don’t have to shop around between dozens of competing solutions for every single piece of your stack, because there are well-documented official solutions that are designed to work together. (You can still swap them out for something else, of course.) With a progressive framework, your framework-specific knowledge can be applied to projects across the entire complexity spectrum, instead of a narrow subset of it.

There are still a lot left to be improved in 2016 - but it’s only going to get better ;)
---
title: First Week of Launching Vue.js
tags: []
excerpt: |2-

      
        
        
          <p><img src="/images/stats.png" alt="GitHub visitors graph"></p>
  <p>I just launched an open source project that I’ve been working on for qui
        
      
      
date: 2014-02-12 05:51:12
---

![GitHub visitors graph](/images/stats.png)

I just launched an open source project that I’ve been working on for qui
<!-- more -->
![GitHub visitors graph](/images/stats.png)

I just launched an open source project that I’ve been working on for quite some time: Vue.js. It’s a library for building web interfaces using MVVM data bindings with a very simple API. If that sounds interesting to you, you can check out more details at [vuejs.org](http://vuejs.org) and the [GitHub repo](https://github.com/yyx990803/vue). The motivation and reasoning behind the library is probably best explained in a separate post - this post is mostly about the personal experience of my first serious attempt at building, launching, marketing and maintaining an open source project.

## [](#Before-Launch-Preparations "Before Launch Preparations")Before Launch Preparations

### [](#Marketing-Plan "Marketing Plan")Marketing Plan

Almost two years ago I [recreated the Clear iOS app with HTML5](https://vimeo.com/37182785) and it enjoyed a decent level of PR success. It all happened without a plan though: I hacked the rough initial version in 2 days, posted a video on Vimeo, and then tweeted at the guys who made the original app. It was not really a serious open source project, more like a shoot-and-forget demo. Then the next day it showed up on HackerNews front page and I got blasted by emails.

Now that I think about it, the reason it worked was because native-like HTML5 interface was still new to a lot of people back in 2012. But this time it’s totally different. The JavaScript MV\* space is totally over-saturated as of now. Although I do believe Vue.js offers something unique to the table, it can be a challenge to convince people to even give it a try. To cope with that I would need to actively promote the project instead of waiting for things to happen. The Mozilla blog had an [excellent post](https://hacks.mozilla.org/2013/05/how-to-spread-the-word-about-your-code/?utm_source=statuscode&utm_medium=email) on this topic. For my project specifically, I prioritized these channels:

*   HackerNews
*   Reddit /r/javascript
*   EchoJS
*   The DailyJS blog
*   JavaScript Weekly
*   Maintain a project Twitter account

The details of these channel’s respective impact will be talked about later in this post.

### [](#Website-and-Documentation "Website and Documentation")Website and Documentation

The website is built with [Hexo](http://zespia.tw/hexo/), a nice static site generator which is essentially Jekyll in Node.js. This allows me to write documentations and guides in Markdown while retaining full control over the site - including visual design and embedding examples. The documentation is written separately in Markdown because personally for me writing all the docs in source comments hurts code readability quite a bit. The site is hosted on GitHub pages. It is also [open sourced](https://github.com/vuejs/vuejs.org) so users can contribute to the contents. One day after launch I got [a pull request fixing Bruce Lee’s email address](https://github.com/vuejs/vuejs.org/pull/3/files). You see, open source is awesome.

### [](#Tests "Tests")Tests

There’s no way people would use an MV\* library without decent test coverage, so for Vue.js a comprehensive test suite is a must. It was fun and exciting when I was hacking away in the beginning, but when the internal architecture stablized I knew I had to start writing tests. I started running Mocha unit tests in a headless PhantomJS instance with `grunt-mocha`. After the API matured a bit, I added functional test cases with CasperJS, and later on switched the unit test runner to Karma so I can automatically run unit tests in real browsers (which is awesome). The code currently has a 96% coverage.Shortly before launch I configured the unit tests to be also run on SauceLabs in all target browsers to ensure compatibility. Gotta have those shiny `build: passing` badges in the README!

## [](#The-Week-After-Launch "The Week After Launch")The Week After Launch

### [](#Day-1 "Day 1")Day 1

**Stats:**

*   Vuejs.org unique visits: 10245
*   GitHub Stars: 212 (+181)
*   GitHub unique visits: 1880
*   Star Rate: 9.6%

**Exposure:**

*   HackerNews front page
*   Reddit _/r/javascript_ top spot
*   EchoJS top spot

I submitted the website link to HackerNews, EchoJS and the _/r/javascript_ Sub Reddit on Sunday Feb 2nd, in the late evening, because I just finished writing the documentation. Had I done enough research, I would have realized it was probably [one of the worst time choices to submit links](http://nathanael.hevenet.com/the-best-time-to-post-on-hacker-news-a-comprehensive-answer/). Luckily, the HackNews submission still made the front page and stayed on it for quite a few hours. The EchoJS and _/r/javascript_ submission both climbed to the top spot, both very encouraging signs. The peak visits/hour was at 9AM Monday, which falls in line with the analysis in the previous linked post. Based on Google Analytics data from now (Feb.11th), about **41.42%** of the traffic were identified as direct visit, among which a large portion probably came from HN. Reddit accounts for **10.08%**, and EchoJS only **1.81%**.

Despite over 10k unique visits to the website in Day 1, the repo only got 1.8k visits. Compared with the following days this is a particularly low conversion ratio. The possible cause was that when the site was first launched, the examples section only had three text links with source directly linked to GitHub. Even worse, the front page also had no code example at all. Google Analytics data shows that among all the visitors that stayed after landing at the home page, **nearly 50% visited the examples page next.** I think having interactive examples like the current [jsfiddle embeds](http://vuejs.org/examples/) would probably help visitors grasp the gist of the library much better.

### [](#Day-2 "Day 2")Day 2

**Stats:**

*   Vuejs.org unique visits: 2892
*   GitHub Stars: 382 (+170)
*   GitHub unique visits: 1266
*   Star Rate: 13.4%

**Exposure:** Featured on [_DailyJS_](http://dailyjs.com/2014/02/03/vuejs-beautify/) blog.

I submitted Vue.js to DailyJS on Day 1 and it was featured on Day 2. The aqcuisition stats up to today show that DailyJS made up for around **4.77%** of total website visits. It is worth noting that visitors acquired from DailyJS had the highest pages/visit (4.64) and the lowest bounce rate (17.01%) among all referral sources. DailyJS also generated 500+ unique visits directly to the GitHub repo, which is the highest referral count except for the Vue.js site and GitHub itself. Day 2 also had the highest GitHub visit/star rate so far.

### [](#Day3 "Day3")Day3

**Stats:**

*   Vuejs.org unique visits: 1257
*   GitHub Stars: 420 (+38)
*   GitHub unique visits: 455
*   Star Rate: 8.3%

There was nothing too exciting on Day 3. I reached out to a few more sources including the Changelog, Smashing Magazine and Peter Cooper ([@peterc](https://twitter.com/peterc), curator of the JavaScript Weekly newsletter). The Changelog agreed to cover the library but nothing happend so far. Smashing Magazine made no response. Peter responded that they’ve already queued Vue.js for the week.

### [](#Day4 "Day4")Day4

**Stats:**

*   Vuejs.org unique visits: 1512
*   GitHub Stars: 459 （+39）
*   GitHub unique visits: 330
*   Star Rate: 11.8%

**Exposure:** Tweeted by [@JavaScriptDaily](https://twitter.com/JavaScriptDaily).

Day 4 @JavaScriptDaily (49.6k followers) tweeted about Vue.js. By this time, Vue.js have had a fair amount of retweets about it, and for all time data Twitter referrals account for about **10.69%** of total visists. However, Twitter visitors had a whopping 55.28% bounce rate and only 2.72 pages/visit, lowest among top 10 referral sources.

### [](#Day5 "Day5")Day5

**Exposure:**

*   Featured in _JavaScript Weekly_ email newsletter.
*   Vue.js TodoMVC benchmark on _/r/javascript_ front page

**Stats:**

*   Vuejs.org unique visits: 2825
*   GitHub Stars: 518 (+59)
*   GitHub Unique Visits: 495
*   Star Rate: 11.9%

The [JavaScript Weekly](http://javascriptweekly.com/) newsletter has a really large audience (>65k subscribers). So far referrals identified from JavaScript Weekly account for **10.42%** of the traffic, the highest among all referral sources. (It is a bit puzzling because it doesn’t show up in the web version of Google Analytics but is included in the Android version.) As a result the falling site visits and GitHub star count saw a decent comeback on Day 5.

As expected, the [TodoMVC benchmark](http://vuejs.org/perf) stirred up some controversy. People love and hate benchmarks - it all depends on whether the results fit their expectations. Having said that, I readily admit these benchmarks do not reflect the whole picture (in fact a very limited case) and should be taken with a grain of salt.

### [](#Day6 "Day6")Day6

**Exposure:** Landed in [TodoMVC](http://todomvc.com) and retweeted by @tastejs.

**Stats:**

*   Vuejs.org unique visits: 1826
*   GitHub Stars: 581 (+63)
*   GitHub Unique Visits: 552
*   Star Rate: 11.4%

Day 6 is pretty exciting because Vue.js landed in TodoMVC. I actually submitted the pull request on Day 1, but it took a week to finally get merged in. I implemented TodoMVC with Vue.js very early on as a testbed for designing the API, and had a pretty comprehensive CasperJS test suite for it that was run on every commit. Interestingly, when I submitted my pull request, the TodoMVC team had just started screening submissions with an automated WebDriver test suite. Thanks to the CasperJS tests it didn’t take me much time to pass all their tests.

I haven’t found a way to quantify the implication of being included in TodoMVC, but based on the traffic it’s not too dramatic. Nonetheless, this is a really good testimonial for the competence and value of Vue.js, considering it was accepted right after the TodoMVC team wrote a post on [Yet Another Framework Syndrome](http://blog.tastejs.com/yet-another-framework-syndrome-yafs).

### [](#Day7 "Day7")Day7

*   Vuejs.org unique visits: 1529
*   GitHub Stars: 615 (+34)
*   GitHub Unique Visits: 399
*   Star Rate: 8.5%

Sunday everything slowed down, which is likely a natural weekly pattern. What’s exciting though is that Vue.js merged the first pull request from the community. In fact, three pull requests were merged or partially included on Day 7. People have also started to hang around in the #vuejs IRC channel, discuss issues and ask questions. There’s certainly some momentum going on :)

## [](#Acquisition-Stats-as-of-Feb-11th "Acquisition Stats as of Feb 11th")Acquisition Stats as of Feb 11th

![](/images/sources.png)

## [](#Now "Now")Now

Since I released Vue.js I have received kind words and suggestions from many people. Considering the current state the JavaScript MV\* scene, the reception has been well beyond my expectation. To all of those who like it, I want to say thank you. And finally, thank **YOU** for reading this far. If you made it here, I assume you are somewhat interested in Vue.js - so checkout the site at [vuejs.org](http://vuejs.org), get in touch via [@vuejs](https://twitter.com/vuejs), or even better, contribute on [GitHub](https://github.com/yyx990803/vue).
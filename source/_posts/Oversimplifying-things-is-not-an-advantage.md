---
title: Oversimplifying things is not an advantage
tags: []
excerpt: |2-

      
        
        
          <p style="text-align:center"><img src="/images/riot.jpg" style="width:200px;display:inline-block"></p>

  <p>I seriously thought <a href="http
        
      
      
date: 2013-11-04 19:31:45
---

![](/images/riot.jpg)

I seriously thought
<!-- more -->
![](/images/riot.jpg)

I seriously thought [Riot.js](https://moot.it/blog/technology/riotjs-the-1kb-mvp-framework.html) was a parody making fun of all the gazillions of MV\* frameworks out there. Turns out it is not — obviously they are pretty serious and published a lengthy blog post discussing how awesome their framework is compared to other popular ones. I guess anyone would be intrigued by how much they can do with just 1kb of code. But does it really hold up to the claims? I quickly checked out the source code and its TodoMVC implementation. Well, you probably already know my conclusion from the title of this post.

I have no problem with the library’s implementation itself. In fact I am a big fan of a minimal boilerplate + compose-it-yourself approach to developing applications. For smaller-scale projects this gives you maximum flexibility to adapt to changing needs, and brings in minimum amount of cognitive barriers. These are real benefits. But at the same time you will have to spend much more time thinking about the implementation details and how to structure your code to keep it maintainable as the codebase grows. There’s nothing wrong in choosing this approach under the right situation, but it is simply a tradeoff rather than an advantage. **The real problem with Riot.js is that its authors are marketing a project with major tradeoffs as if it’s superior in every aspect, with hyperboles and misleading comparisons**.

**Less to Learn**. Sure there’s less to learn about the framework itself, but there’s also so much more to learn outside of the framework! The equivalence of “less to learn” is “we are not really offering much”. Talking about MVP when you don’t provide actual implementation is like saying “You should have a model, a view and a presenter, but you have to figure out how to build them yourself.” That’s pretty helpful, thank you Riot.js! If I already know how to implement a model, why would I even need you?

**Less proprietary idioms.** Frameworks enforce idioms and conventions so that multiple team members using the same frameworks will understand the same set of concepts and can understand each other’s code more easily. It’s an initial commitment to smooth out later collaboration costs. When too little is abstracted away and too much is up to the developers, you will end up having to dig into other people’s implementation details to understand what’s really going on once the codebase starts to grow, and that will cost more than the initial hours spent learning the framework.

**Less bugs.** Sure, less bugs in the framework. But again, what about outside of it? When you have direct jQuery manipulations scattered all over the place in the Presenter? There’s in fact no so-claimed “auto updating view” because you have to manually emit change events. The more logic the developer has to manage, the more bug prone the entire project is. By delegating logic bookkeeping to the frameworks via features like computed properties, we are transferring a part of the debugging burden to the frameworks, which most popular ones have solid test coverage and a community reporting bugs for them. What Riot.js is doing is simply putting the burden of making sure things work back to the developer, and I wouldn’t call that an advantage.

**Embeddable.** When you have jQuery as a hard dependency? That alone makes its size close to Angular.

**Faster.** Oh of course, let’s all write our applications in asm.js, that’s going to be damn fast! On a more serious note, again you are making tradeoffs. You have to weigh in how much functionality you are giving up before you talk about speed. Eviltrout already pointed out it’s simply unfair to compare Riot.js’ templating function to other engines because it doesn’t even do loops, partials or conditional statements. Also with Riot.js you are throwing away entire chunks of DOMs and recreating them on every refresh, and what happens when you have thousands of elements in a single view and you are only updating one value? That’s terribly inefficient.

**Cheaper.** Good luck building an Amazon-scale application with Riot.js. You’ll probably spend more money on additional refactor hours than the saved bandwidth cost.

**Clean separation.** I want to emphasize that the framework itself does not enforce anything. You can’t claim that a framework does X because something that utilizes X can be written while accidentally using the framework. The framework has to enforce X as an obvious or even inevitable choice to qualify for that claim. I can write MVP style code with a simple event emitter library too, can I call it an MVP framework? In Riot.js’ case the MVP separation is in no way exemplified in the source code itself, and even when using it you can still easily end up with shitty code unless you are already good enough to have clean separation without it.

**Less application code.** Let’s take a look at the TodoMVC example. The example itself is still missing features as of this writing, and against what the site claims it actually uses more SLOC than Angular’s both TodoMVC implementations. You have to manually emit model changes. There’s no computed property so you have to manually keep track of updating all the properties that depend on other properties (the counters). You have to manually create, inject and modify the DOM or listen for events in a ton of places. By scattering selectors all over the place the HTML template and the JavaScript code is tightly coupled so when you change one place you need to manually change the other place as well. Let’s admit that the gzipped code size is not an accurate metric to reflect the amount of work you need to do as a developer, neither is TodoMVC a good indicator for how well a framework can deal with large scale applications.

I’d like to repeat that I have no problem with a minimal approach in building web applications. I’m just really bothered by the way Riot.js is being marketed. If you are a novice and need help from a framework, it offers too little guidance; If you are a competent developer, it offers too little functionality. The advantages it’s boasting are in fact tradeoffs.To me its use case is really narrow and the value it offers doesn’t justify the hype it gets.
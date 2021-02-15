---
title: DOM Composition Events compatibility notes
tags: []
excerpt: |2-

      
        
        
          <p style="text-align:center;padding:30px 0 40px"><img src="/images/composition.png" style="width:374px;display:inline-block"></p>

  <p>If you
        
      
      
date: 2014-01-03 19:49:42
---

![](/images/composition.png)

If you
<!-- more -->
![](/images/composition.png)

If you don’t frequently type in a non-latin language, e.g. Chinese, then most likely you’ve never heard of [Composition Events](https://developer.mozilla.org/en-US/docs/Web/API/CompositionEvent). Even for a Chinese developer, it’s rare that these events are needed in development. In fact I didn’t learn about their existence until recently, when I was trying to alter an input field’s value as the user types. Everything works perfectly when typing English letters, but it turns into a mess when I tried Chinese. Let me explain.

The way IME composition works is that it buffers the user’s keystrokes until a character/word selection has been made, finalizing the input. The buffered keystrokes are temporarily displayed, but not actually inserted into the DOM. However, when I change the input field’s value during a composition, the composition gets terminated early and these buffered keystrokes get inserted into the input field.

As I was banging my head against the wall trying to find a solution using key events and async updates, I discovered composition events. They are exactly what I need! But not before I get bitten by the various inconsistencies across major browsers. According to the [spec](https://dvcs.w3.org/hg/dom3events/raw-file/tip/html/DOM3-Events.html#event-type-compositionstart), this is the expected behvaior:

*   fire `compositionstart` when composition starts.
*   fire `compositionend` when user selects a character/word and finalizes the input.
*   fire `compositionupdate` on every input during composition, including immediately after the start event and immediately before the end event.
*   `input` events should fire after composition events

What’s actually implemented in major mordern browsers:

*   **Firefox 26** : working according to the spec.
*   **Chrome 31 / Safari 7** : doesn’t fire `compositionupdate` immediately after the start event or before the end event. For `compositionstart`, the event’s `data` value is wrong (`undefined` where an empty string is expected).
*   **IE10** : fires only one `compositionupdate` right after `compositionstart`, then no more.
*   **IE9** : fires `input` before composition events.

Pretty annoying, but luckily not too complicated to work around with for my case. All I had to do was listening for `compositionstart` and `compositionend` and avoid changing the input field’s value during the whole composition - and voila, problem solved!
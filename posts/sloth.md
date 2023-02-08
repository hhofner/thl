---
layout: index.njk
title: Sloths
tags: ['post', 'japanese', 'vue']
date: 2023-02-07
---

Did you know that Hamsters have a heart rate of 400bpm? Neither did I, and that's actually very impressive when you consider a humans average resting heart rate is 72. 

I've heard this idea that humans, and animals in general, have a set amount of heart beats. It sounds like it makes sense, if you consider us to be like machines. 

Unfortunately this silly idea doesn't entirely hold true, because then otherwise athletes as a whole would die earlier (since they do more exercise than an average person does, thus quickly depleting their heart beats).

At least, according to this research article, it doesn't hold true:[Health Consequences of an Elite Sporting Career: Long-Term Detriment or Long-Term Gain? A Meta-Analysis of 165,000 Former Athletes](https://link.springer.com/article/10.1007/s40279-020-01379-5)

But this brings me to my main point, Sloths have a heart beat of around 20bpm, maybe higher, that paired with the idea that Sloths try to conserve as much energy as possible, I expected them to live longer. Unfortunately, they live about 20 years, which I found to be a bit short.

<hr/>

I learned that if you'd like to access the store of a module in a Vuex store, via the object that is created from the Vuex constructor, you do it via the state attribute and not from the modules. In other words:

```javascript
const store = Vuex.Store({...})

// Not this
const stateIWant = store.modules.someModule.state

// But like this
const stateIWant = store.state.someModule

```

<hr/>

I often find myself bouncing between Sublime Text, VSCode and Neovim. 

You'd think Sublime Text is a good middle ground, and it is in most cases, but not always.


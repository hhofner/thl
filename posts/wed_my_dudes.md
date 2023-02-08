---
layout: index.njk
title: Wednesday My Dudes
tags: ['post', 'life', 'vue', 'vuex']
date: 2023-02-08
---

I finally encountered a situtation in where hoisting poses a problem. In a Vue 2.7 codebase, we are trying to migrate unit tests from Vue 2 to Vue 3. Unfortunately, this means we have to figure out how to use Vuex and other tools that were meant for Vue 2 in Vue 3, and additionally understand how to mock these certain plugins in Jest. 

Vuex posed a small issue in that the newly written composition API components, the store object is directly imported from the main file that exports the Vuex store object. 

While that works fine, it's a bit awkward in Jest (vue-test-utils) testing.

Usually, you'd provide a `store` object direcyly to `createWrapper` provided to by vue-test-utils, but since the component we are testing only reaches the Vuex store by means of direct import, that provided `store` in the wrapper method does nothing. 

So you have to mock it, and to mock an entire store gets really cumbersome, because you are essentially rewriting a Vuex application. This is where the main issue lies:

Ideally, we'd do something like this:
```javascript
import ComponentToTest from "./ComponentToTest"

// in your .spec.ts file
Vue.use(Vuex)
const store = Vuex.Store({...})

jest.mock('@/store', () => store)
```

Unfortunately, this doesn't work because you get a reference error that you can't reference `store` before initialization. 

The reason this happens is because `jest.mock` are hoisted up. Whenever you import the `ComponentToTest`,you are calling `import store from "@/store`, which then calls the mock. Since you haven't defined the store yet in, this error occurs. 

So a simple, and hopefully temporary solution to this is...to just move up the store call before the import. 

```javascript
// in your .spec.ts file
Vue.use(Vuex)
const store = Vuex.Store({...})

import ComponentToTest from "./ComponentToTest"

jest.mock('@/store', () => store)
```

and it works. Hopefully it doesn't cause any big problems in the future, and since it's a unit test, you can just delete it if it doesn't work :) 

Happy wednesday.


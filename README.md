# Vue3-guide

## Composition API

### Instalation 

<i>yarn add @vue/composition-api </i>

- Vue2 is very spilt up in the proejct

- Using the composition API we can make our components much more readable.
- We write composition functions outside the setup method.  
- You are able to use Vue2 solutions like Mixin's and mixin factories and scoped Slots in vue3.
- BUT in Vue3 we have Composition functions. We can use composition functions and use them in the setup for configuration of const's and more. 

## Setup & Reactive References 

When do we use the Compsition API? 

- It's a second way to write components.. You can still write component's in the old way. 

What is good about the composostion API? 
- Typescript support 
- Component is too large and needs to be organized by feature. 
- Need to reuse code across other components. 

Setup() executes before : Components, Props, Data, Methods, Computed Properties & Lifecycle methods. <br>
The Setup() method does NOT have access to "this" which means that the structure is a little different. 

## Methods

Methods are executed as functions in the new Composition API. We can write our functions inside the setup() function and make our setup() return a value which goes thorugh the function. More about functions can be found with the following link:

https://www.vuemastery.com/courses/vue-3-essentials/methods/

## Computed Properties 

We can create and manipulated computed properties directly from the setup() functions. We can take a "computed" function and put equal to a constant. We can then manipulate the constant and make use of it in the DOM by returning it from the setup() method. 

## The Reactive Syntax 

To make the app reactive we need to return an event with a function to be able to let the DOM react live in terms of changes. We will therefore have to activly make use of "event" in our code like in a v-for="(name, index) in event.attending" :key="index". 

We are also introduced to the <b>toRefs</b> method which converts a reactive object to plain object, where each property is a Reactive Reference pointing to the property on the original object. 

https://www.vuemastery.com/courses/vue-3-essentials/reactive-syntax

## Modularizing 

The Composition API is very open for modulization, and the api enables us to create functions outside the export default {}. The setup() method now becomes the place where I tie my composition functions together. 
This enables us go create reusable code which we can use in multiple components. 

If we have a function eg. doSomething() i would just have to extrat that function into it's own file which export default. 

It's quite simple to share composition functions across you'r components. Realistically i'd probably have shared data which i'd send these funtions, like the event data which has fetched from an API using Vuex. 

https://www.vuemastery.com/courses/vue-3-essentials/modularizing

## Lifecycle Hooks 

We are all probably familiar with Vue lifecycle hooks, but they have been changed to the following:

- beforeCreate - Called immediatly after instance is initialized, before options are processed. 
- created - Called after the instace has been created. 
- beforeMount - Right before mounting of the DOM begins. 
- mounted - Called when the instance has been mounted (browser updated). 
- beforeUpdate - Called when reactive data has changed, before the DOM is re-rendered. 
- updated - Called when reactive data has changed, and the DOM has been re-rendered. 
- beforeDestroy -> onBeforeUnmount - Called right before the Vue instance is destroyed. 
- destroyed - Called after the Vue instance has been destroyed. 

There are newer Vue2 lifeCycle: 

- activated - Used for, when a component inside is toggled on. 
- deativated - Used for, when a component inside is toggled off. 
- errorCaptured - Called when an error from any descendent component is captured. 

More details can be found here:

https://vuejs.org/v2/api/#Options-Lifecycle-Hooks

In vue 3 beforeDestroy() can also be written as beforeUnmount(), and destroyed can be written as unmounted().

In Vue 3 we make use of the lifecycle hooks inside the setup() function.

There are two more additional watchers comming in vue 3. These have not been implemented with the Vue 2 Composition API plugin (as I’m writing this), so you can’t play with them without using Vue 3 source.

- onRenderTracked - called when a reactive dependency is first being accessed in the render function, during render. This dependency will now be tracked. This is helpful to see which dependencies are being tracked, for debugging.

- onRenderTriggered - Called when a new render is triggered, allowing you to inspect what dependency triggered a component to re-render.

## Watch

With base implemented API code, the code is only called once when setup is run. We need it to run every time the search input changes and this is where we use watch to keep track of data that changes. I use watch as an annonymous function on a value. 

It means that a watch function is run on next tick whil reactivly tracking its dependencies, and re-run it when its dependencies change. 

- We can be specific about what riggers the watcher to run.
- We can get access to the new value and old value of the item being watched. 
- We can specifically watch two rective references at once.
- We can also watch reactive references with access to new and old values.

## Sharing State

Sharing state with the composition API means that we create a promis in a file which sends in the function to call with async/await. 

We can then import the promis file which holds state data in form of constants. In the component we will then call the promise with updated searchinput data. 

# Vue.js presentation 2019-Q3
My name is **Maxim Shilov** and I am a RSS student. Now I’ll tell you about Vue.js

`(Next slide)`

What is Vue.js?

`(Next slide)`

Vue.js is a progressive javascript framework for building user interfaces.

`(Next slide)`

Let's start with history. The creator of Vue.js is Evan You.

`(Next slide twice)`

He worked as a creative technologist at Google. From 2016 he works full-time on vue.js framework.

`(Next slide)`

Work on Vue.js was launched at the end of 2013. The first release came out in February 2014. The latest release is version 2.6.10

`(Next slide)`

Vue.js is currently used by companies such as:
+ Grammarly
+ 9GAG
+ Behance
+ Laravel Spark
+ GitLab
+ Offers.com
+ Nintendo
+ Adobe
+ Euronews
+ And many more

`(Next slide)`

It also used on Belarusian websites:
+ Onliner.by
+ 5element.by

Perhaps, it’s already used on more websites, I’m not sure.

`(Next slide)`

Core features of Vue.js are:
+ MVVM-like architecture
+ Сomponent approach
+ Reactivity

`(Next slide)`

MVVM is a design pattern in which an application is divided into 3 parts:
+ model (as in the MVC pattern, it is a data source, contains business logic and updates from viewModel)
+ view (the visual interface. In this case, this is the visual component of the web page with which the user interacts, it does not process events, but only generates commands based on user actions)
+ viewModel (it connects the model and the view, being a layer between them, and, based on the commands from view, updates the model)
MVVM is implemented through vue instances that control certain elements of the page. Instances contain a viewModel and a model and the DOM contains view part.

`(Next slide)`

Сomponent approach

`(Next slide)`

Components are named vue instances that can be used as separate elements within the root instance. It’s easy to reuse them. Each of this components can work regardless of the others with its own set of source data. Components can and should be nested one to another, it contributes to better code organization.

`(Next slide)`

Vue-cli or webpack allow you to use single-file components (files with the * .vue extension containing html markup, styles and js-code of a separate component for assembly).

`(Next slide)`

Here is example of how it looks like

`(Next slide)`

Reactivity

`(Next slide)`

Vue.js allows you to declare model data **reactively**, thus you don’t need to follow up on your own (only if you do not want a deeper adjustment) for updating the **data** in the model, because the properties specified in the data property of the instance during its initialization (as well as you want to add them using a special method) are converted to getter-setter pairs, due to which Vue.js watches data dependencies and changes and updates them on its own in a timely manner.

`(Next slide)`

How does vue.js work?

`(Next slide)`

It all starts with initializing the vue instance to which the options object is passed.

Instance goes through the certain stages of the life cycle.
As you can see on the diagram, the vue instance goes through certain steps, between which functions named **lifecycle hooks** are called: at first, events and life cycle are initialized (**beforeCreate** hook), then injections and reactivity systems (**created** hook) are initialized, then vue engine checks el and template option presence (they contain the element into which the template will be compiled, or something from which outerHTML will be compiled),then the **beforeMount** hook triggers, after which vm.$el is created (vm is the designation for instance, system properties and methods of which start with a "$"), which replaces the contents of the **el** element. After that, the **mounted** hook triggers, it means that the instance is initialized and ready to work. 

Then, as the instance data is updated, the **beforeUpdate** and **updated** hooks are called, and then changes are applied to the instance by updating the virtual DOM. When you need to destroy the instance, it can be done by calling the **vm.$destroy** method. 

After that, the **beforeDestroy** hook triggers, in which you can handle all communications of the instance, after that they all will be deleted. After all this data is deleted, the instance is destroyed, and then **destroyed** hook triggers. **Lifecycle hooks** are like real life “hooks” on which we can suspend the necessary functionality in the certain points of the lifecycle.

`(Next slide)`

Most of the vue instance functionality is implemented using several fields

`(Next slide)`

**Data** field contains data properties

`(Next slide)`

In this example, you can see how information from properties gets into the DOM.

`(Next slide)`

**Methods** field contains functions that are bound to vue instance. Like all javascript functions, they may accept parameters and will be re-evaluated every time they are called 

`(Next slide)`

In this example you can see the use of a method for making counter

`(Next slide)`

When we press the button, the value increases

`(Next slide)`

**Computed** field contains computed properties whose value is generated dynamically. Unlike methods, they are not executed with every call, but updated only with changes in their dependencies.

`(Next slide)`

Here we see a classic example with the calculation of the **reversedMessage** property based on the **message** property. 

`(Next slide)`

Besides that, this computed property returns a value to us, it also allows us to set values using the **get / set**:

`(Next slide)`

A setter triggers and updates the **firstName** and **lastName** properties,when you assign a value to the **fullName** property.

`(Next slide)`

**Watch** field contains observer functions whose code executes when the observed properties change.

`(Next slide)`

In this case, watcher will trigger on every change of the message property value and alert will be shown.

`(Next slide)`

Lets try it!

`(Next slide)`

Lets talk about some other features of Vue.js

`(Next slide)`

First of all, **declarative rendering**

`(Next slide)`

You can transfer data from instance into elements

`(Next slide)`

In this example you can see how data from “message” property gets in the DOM using mustache templates.

`(Next slide)`

You also can dynamically bind the attributes of the elements

`(Next slide)`

In this example, you can see that the data from "message" is attached to the "title" attribute.

`(Next slide)`

The next important feature is the **directives**:

`(Next slide)`

Vue.js has Angular-like directives which are html attributes starting with the "v-" prefix and adding special reactive functionality to the elements that contain them. Some directives also have shorthand names.

`(Next slide)`

A short list of frequently used directives and their functionality:

`(Next slide)`

Directives that control presence of an element are **v-if**, **v-else**, **v-else-if**, **v-show**

`(Next slide)`

V-if determines if an item will be rendered. If the value of its expression in the logical context is false, the element is not rendered and does not appear into the DOM. V-else can be used along with v-if and it triggers when value of v-if expression in the logical context was false. V-show, depending on the truth of the condition, sets the value of the visibility property to hidden.
As you can see, a div that contains "A" has been drawn. Secret div stays hidden.

`(Next slide)`

V-for directive

`(Next slide)`

V-for directive allows you to generate elements based on ordered data structures, such as arrays

`(Next slide)`

This example shows how data from an array goes to the DOM

`(Next slide)`

V-on directive

`(Next slide)`

The v-on directive allows you to assign an event handler. Its short form is “@:”

`(Next slide)`

Let's take a closer look at the previous example
In this case, the handler function increases the property recorded in data, then thanks to the Vue.js reactivity system it changes in the DOM.

`(Next slide)`

V-bind

`(Next slide)`

The v-bind directive allows you to bind the attribute value to data in the vue instance. Its short form is ":". 

`(Next slide)`

Let's look at an example with a dynamically bound title again.

`(Next slide)`

V-model

`(Next slide)`

Using the v-on and v-bind directives, we can bi-directionally connect the text entered in the form element (for example, input) with the value of the variable in the vue instance.

`(Next slide)`

In this example, the input value is synchronized with the message property and it is displayed in paragraph below

`(Next slide)`

To write such a combination, there is a v-model directive, which in this case is the syntactic sugar for the v-on and v-bind combination. 

`(Next slide)`

This code does the same as previous

`(Next slide)`

Still works

`(Next slide)`

There are other directives such as:
+ v-text
+ v-html
+ v-slot
+ v-pre
+ v-cloak
+ v-once

They are used less often.

`(Next slide)`

Directives may also have modifiers - a kind of flags that modify the directive behavior.

`(Next slide)`

In this case, the v-model does not trigger on the input event, but on the change event, thus the data will be updated, for example, when focus is lost on the input, instead of synchronization of each character.
Let’s try to write something. Now it is not updated immediately, but is updated with loss of focus.

`(Next slide)`

More detailed info about directives and documentation can be found on the official website at:
+ https://vuejs.org/v2/guide/
+ https://vuejs.org/v2/api/
+ https://vuejs.org/v2/style-guide/
+ https://vuejs.org/v2/examples/
+ https://vuejs.org/v2/cookbook/

`(Next slide)`

Vue.js also has a rich environment:
+ vue-cli - vue command line interpreter, a shell for work with the command line;
+ vue-devtools - as the name implies, developer tools for debugging applications, browser extensions like Chrome devtools, but made specially for convenient debugging of code written with using Vue.js
+ vuex - redux-like application state storage 
+ vue-router - provides routing for single page application
+ vue-server-renderer - server-side rendering (SSR)
+ vue-loader - single file components (files *.vue) loader for webpack
+ vue-rx - RxJS integration tool
+ and much more...

`(Next slide)`

Let's summarize.

`(Next slide)`

Pros of Vue.js are:
+ High performance (on the same level (and sometimes better) of such giants as React and Angular)
+ Very small size - vue2 + vuex + vue-router weighs ~ 30kb in gzip format. The minified vue2 weighs ~ 20kb in gzip format
+ Easy to learn - it’s easier to start with Vue than with React or Angular; all you need to know for quick start is basic html and css, and JS at the ES5-ES6 level
+ Full and detailed documentation
+ Flexibility – Vue.js can be used either as a library for creating reactive components on a webpage, or as a framework for creating SPA.

`(Next slide)`

Cons of Vue.js are:
+ Reactivity does not cover all of the necessary data, and sometimes you have to rewrite the code to achieve the desired application behavior, and some things are quite difficult to implement. However, the reactivity system in vue3 will be implemented on Proxy, which will more fully cover all the necessary cases;
+ Vue.js is not suitable for extremely complex and highly loaded projects, here it loses to some other frameworks such as Angular;
+ As we know, Facebook has developed and still supports React, as well as Google - Angular. Vue.js was developed by just Evan You. Because of his relative youth and because Vue.js is not a product of giant corporations, it still has a smaller community and less widespread. So, there are fewer vacancies and fewer ready-made solutions.

`(Next slide)`

Thanks for attention!
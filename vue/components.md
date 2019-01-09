## Component Basics
A component is a reusable piece of code that describes a chunk of your application.  On several websites, each element of the page can be thought of as a component.  In addition to just the visible pieces of a user interface, a component can hold other components.  If all they do is hold other components, they can also be called containers.


#### Creating Components
Unlike several other frameworks, component files often have the HTML, JavaScript, and CSS for a given component all in the same file.  This is a stylistic choice that Atom defaults to if you want to quickly create components.  Component files end in `.vue`, so (ideally in a components folder) create a new `.vue` file and type `template` followed by a `tab`.  It should auto-generate a component skeleton.  It should look something like this:
![alt text](component_template.png "yay vue")

#### Component Components
The `<template>` tags are the HTML of the component: the visuals.  This is what your component renders when it is loaded onto a page.  If you want to change the way a component's data is displayed, this is where to look first.

The `<script>` tags hold the behavior of the component.  This section uses JavaScript and can take advantage of ES6 features like the spread operator and arrow functions.  A component's state, methods, and lifecycle behavior are all defined here.  The exported object is the actual object that other files will interact with.

The `<style>` tags hold the styling of the component.  I use CSS to style my components, but that's only because I don't know SASS/SCSS, and I hear those require additional styling files.  I suppose it would be more practical for components with an assload of styling, like supporting themes or something, but for something simple, CSS does the job well enough for me.

#### The Template
There are a few simple things to know for the `<template>` section.
1. Everything must be in a single wrapping tag.
![alt text](template.png "notice the wrapping div")

Both the `h1` and `p` tags will render, but without the surrounding `div`, you'll get an error.  Everything must be encompassed by one tag.

2. You can use mustaches to include variable data.
![alt text](mustaches.png ":{")

We'll get to where the data comes from in a little bit, but depending on the value of `name`, the template will render something different.  This is helpful!

3. Directives can be used for conditional rendering.
![alt text](conditional.png)

The `v-if` and `v-else` attributes you see in the tags are called **directives** in Vue.  There are several other directives, but we'll cover them later.  As you can see, depending on the value of `name`, a different `h1` will be rendered.  Between the single quotes in the `v-if` directive are JavaScript expressions, and any valid JavaScript expression can be used here.

#### The JavaScript Part
This is where the logic of a component gets placed.  Vue components are objects with several other object fields.  A few of them are:
1. `components` - if the component uses other components, they must be registered here.
2. `props` - if the component is to receive props (more on this later), this is where you register those props and do optional type checking.  For simple use, it's an array of strings that label the expected props.
3. `data` - if your component needs to store local state, it is done through a `data` *function*.
4. `methods` - if your component has methods that go with it, they get written here.

I know this is a lot to take in, but altogether it'll look something like this:
![alt text](ree.png "it's daunting but it's simple :')")

###### A note on props
Props (short for properties) are bits of information passed to a component that it may not know ahead of time.  In the template section, the `name` variable might be passed to the component as a prop.  If the `name` prop is passed as the string `Jessica`, then `Jessica` will be rendered.  We will expand on this later.

Not all of these sections are required for a component to work, for example a component may have no methods or data to store.  

#### The Style
This is where your styling goes.  If you know CSS, it's just a css file starting here.  No special rules or anything.  Easy!

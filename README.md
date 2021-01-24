# vue-modal-project

From The Net Ninja: Vue JS Tutorial for Beginners #4 @ https://www.youtube.com/watch?v=GWRvrSqnFbM

Initial Creating Steps 
Install npm and node

Creating a new site via the vue cli
npm install -g @vue/cli

Install Vetur package from extentions

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### Notes
* Public/index.html: Where the app is injected  
  `<div id="app"></div>`
* src folder: Where app is written  
* main.js: JavaScript file that kickstarts the application with the `createApp(App).mount('#app')` method  
* App.vue: This is the root component

---
## Basic component importing
https://codesandbox.io/s/basic-component-importing-d3ui7

1. Import the component into the app file
2. Put the component into a the template like this: `<someComponent></someComponent>`
3. Add the component to the export default object:
```
export default {
  components: {
    someComponent: someComponent
  },
};
```
4. Create the component file with a .vue extension under the components folder. Include template, scripe, style.

---
## Basic script data 
1. Add the property to the data function in the script
```
  data() {
    return {
      title: "This is the title!"
    }
  },
```
2. Output to the template `<p>{{ title }}</p>`

---
## Use Refs to get references to DOM elements
1. Use ref="nameCanBeWhateverYouLike" on an DOM element: 
```
<input type="text" ref="templateRef"><button @click="handleClick">Click</button>
```
2. Do JavaScript things with the reference using a method:
```
methods: {
  handleClick() {
    console.log(this.$refs.templateRef)
    this.$refs.templateRef.classList.add('active') // add a class that is active
    this.$refs.templateRef.focus() //javascript focus on the ref element
  }
}
```

---
## Styling: Scoped vs Global
See https://www.youtube.com/watch?v=KM1U6DqZf8M

---
## Props and Data Binding
https://codesandbox.io/s/basic-props-b9g33
1. Add Attribute. Here attribute (the prop) is called thisIsAProp
`<Modal thisIsAProp="text data from App.vue"/>`
2. Accept the prop in the component script:  
```
<script>
export default {
  props: ['thisIsAProp']  //should be in quotes
}
</script>
```  
3. Output the prop value
`<p> {{ thisIsAProp }}</p>`

---
4. To use data binding, use the v-bind: or :. Bind to either data in the string, ie :databinding="[1,2,'text',true]" or to a template property.  
`:dataBoundPropToATemplateProperty="aProperty"`  
5. Add the template property
```
<script>
export default {
  data() { 
    return {
      aProperty: "This is a text property"
    }
  }
}
</script>

```
6. Then use steps 2 and 3 above to output the data. 

___
## Conditional Rendering
1. Add conditional rendering with `v-if=""`
```
<div v-if="showDiv">
  Using conditional rendering
</div>
```
2. (Optional) Added an event that connects to a method, to change condition
```
<button @click="showAndHideMethod">Using Conditional Rendering</button>
```
3. (Optional) Add the method to change the condition
```
showAndHideMethod() {
  this.showDiv = !this.showDiv 
}
```
4. (Optional) Added the property for the condition
```
data() { 
  return { 
    showDiv: false
  }
}
```
5. (Optional) Use v-else or v-else-if 
```
<div v-else> <!-- Conditional Rendering 5 -->
  Using else
</div>
```
### Related: v-show 
`v-show=""` uses CSS to `display:block` when a condition is true, and `display:none` when false.
```
<div v-show="showDiv">
  Using 
</div>
```
___
## Click Events
Note: `@click` is shorthand for `v-on:click`  

### Passing in arguments to the event
1. Events like `@click`, `@dbleclick`, `@mouseover`, etc automatically give us access to the event object. Access it in the method with `$event` syntax, it should be passed first. Pass in the param second. 
```
<div @click="someEvent($event, 'some param')">Click Here</div>
```
2. Add the method and (optionally) pass in the event, and then pass in the param
```
methods: {
  someEvent(event, param) {
    console.log(event)
    console.log(param)
    this.updateAParam = param //Updating a param
  }
}
```
3. For reference, here is the data
```
data() {
  return {
    updateAParam: 'please update this value'
  }
}
```

### Using a click event to update a property directly in the template

1. A property in data must exist
```
data() { 
  return { 
    countProperty: 0
  }
},
```
2. Output the data on screen
```
<p>The count is {{ countProperty }}</p> 
```

3. Add the event. Target the property with `v-on:`. Here some JavaScript is running directly inside the `""`.
```  
<button v-on:click="countProperty += 1">Increase Count</button>
```  

### Using a click event with a method
Add 1 and 2 above, skip step 3.

4. Add the event, but it should now call the method.
```  
<button v-on:click="thisIsAMethod">Increase Count</button>
```  

5. Target the property with a method. Add the method to `methods`
```
  methods: {
    thisIsAMethod() {
      this.countProperty -= 1 //target the property inside the method
    }
  },
```

---
## Emitting Custom Events
To get an event to connect to another component:
#### In Parent Component
1. (Optional) Add any property needed to data in the parent component 
```
data() { return { showModal: false }}
```
2.  (Optional) Add the if statement, etc 
```
<div v-if="showModal">
```
3. Add a parent element event: 
```
<button @click="toggleModal">Open Modal</button>
```
4. Add method for parent element click event 
```
toggleModal() { 
  this.showModal = !this.showModal
}
```
5.  Add the method to the child component and connect it to the custom event (named @close)
```
<div v-if="showModal"> 
  <Modal @close="toggleModal"/>
</div>
```
### In Child Component  
6. Emit the custom event from a method
```
methods: {
  closeModal() {
    this.$emit('close') // this is a custom event named close
  }
}
```
7. Add the method to an event in the child component.
```
<div class="backdrop" @click="closeModal"></div>
```
### Click Event Modifier 
Add the modifier to the event, ie .right, .left, .shift, .alt. Use .self to target element directly (and to prevent sub elements from being targeted)
```
<button @click.right="toggleModal">Open Modal With Right Click</button>
```

---
## Slots
Slots- for passing custom templates into components
1. From the parent, add html. If nothing is passed here, then whatever text is in the child <slot></slot> will render.  
App.vue  
```
<template>
  <Modal>
    <h1>Some Text Here</h1>
  </Modal>
</template>
```

2. From the child, the html is displayed in the slot: 
Modal.vue 
```
<template>
  <slot>This text only renders if no text is passed through</slot>
</template>
```

3. Create a named slot by adding the slot directive 
App.vue 
```
<template>
  <template v-slot:thisIsTheSlotName> 
    <a href="#">Named Slot Link 1</a>
    <a href="#">Named Slot Link 2</a>
  </template> 
</template>
```
4. Call the named slot in the child
Modal.vue
```
<slot name="thisIsTheSlotName"></slot>
```
---
## Teleport 
Allows us to move content in the app to somewhere else. All the functionality will still work. 
1. Replace `<div>` with `<teleport to=".modals">`. Targeting the .modals class here. 
2. Add the class to the targeted div. `<div class="modals"></div>` 

---
## The v-for Directive

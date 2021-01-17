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
Public/index.html: Where the app is injected
  <div id="app"></div>
  <!-- built files will be auto injected -->

src folder: Where app is written
main.js: JavaScript file that kickstarts the application with the `createApp(App).mount('#app')` method

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
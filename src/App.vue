<template>

    <div id="app">
      <Modal theme="sale" thisIsAProp="text data from App.vue" :thisIsADataBoundProp="['an','array',1,2,3]" :dataBoundPropToATemplateProperty="aProperty"/> 
      <!-- 
        Props 1:  Add Attribute. Here attribute (the prop) is called thisIsAProp. 
        Data Binding Props 1: :thisIsADataBoundProp is the prop and bound to an array 
        Data Bound To A Template Prop 1: :dataBoundPropToATemplateProperty is the prop and bound to the template property named aProperty
      -->
      <HelloWorld msg="Welcome to Your Vue.js App Yay!"/> <!-- Import component step 2 -->
      <p>{{ title }}</p> <!--Template Property 2 -->

      <input type="text" ref="templateRef"> <!--Template Ref 1 -->
      <button @click="handleClick">Click</button>
    </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue' // Import component step 1
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  data() { //Template Property 1
    return {
      title: "This is the title!",
      aProperty: "This is a text property" //Data Bound To A Template Prop 2: the template data property
    }
  },
  components: { // Import component step 3
    HelloWorld,
    Modal
  },
  methods: {
    handleClick() {
      console.log(this.$refs.templateRef) // Template Ref 2
      this.$refs.templateRef.classList.add('active') // add a class that is active
      this.$refs.templateRef.focus() //javascript focus on the ref element
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

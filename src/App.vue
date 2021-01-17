<template>
    <div id="app">
      <img alt="Vue logo" src="./assets/logo.png">
      <HelloWorld msg="Welcome to Your Vue.js App Yay!"/> <!-- Import component step 2 -->
      <p>{{ title }}</p> <!--Template Property 2 -->
    </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue' // Import component step 1

export default {
  name: 'App',
  data() { //Template Property 1
    return {
      title: "This is the title!"
    }
  },
  components: { // Import component step 3
    HelloWorld
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

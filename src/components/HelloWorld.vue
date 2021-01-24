<!-- Import component step 4 -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
      <p>The count is {{ countProperty }}</p> <!-- Click Event 2 -->
      <button v-on:click="countProperty += 1">Increase Count</button> <!-- Click Event 3. Just target the property with v-on: -->
      <button @click="thisIsAMethod">Decrease Count</button>
    </div>
    <div>
      <p>Using Conditional Rendering</p>
      
      <button @click="showAndHideMethod">Using Conditional Rendering</button> <!-- Conditional Rendering 2 -->
      <div v-if="showDiv"> <!-- Conditional Rendering 1 -->
        Using v-if="", which takes elements of out dom completely
      </div>
      <div v-else> <!-- Conditional Rendering 5 -->
        Using v-else=""
      </div>
      <div v-show="showDiv">
        Using v-show="", which uses CSS to display block when true, and display none when false.
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() { 
    return { 
      countProperty: 0, //Click event 1
      showDiv: false //Conditional Rendering 4
    }
  },
  methods: {
    thisIsAMethod() {
      this.countProperty -= 1
    }, 
    showAndHideMethod() { //Conditional Rendering 3
      this.showDiv = !this.showDiv 
    }
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

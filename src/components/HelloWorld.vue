<!-- Import component step 4 -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>The count is {{ countProperty }}</p> <!-- Click Event 2 -->
    <button v-on:click="countProperty += 1">Increase Count</button> <!-- Click Event 3. Just target the property with v-on: -->
    <button @click="thisIsAMethod">Decrease Count</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() { 
    return { 
      countProperty: 0 //Click event 1
    }
  },
  methods: {
    thisIsAMethod() {
      this.countProperty -= 1
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

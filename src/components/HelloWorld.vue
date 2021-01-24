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
    <div>
      <div @dblclick="passParamIntoEvent($event, 'some param')"> <!-- Pass Params in Events 1. To incldue the event, pass $event first -->
        Double click to pass in a param. It will render {{ here }}
      </div>
    </div>
    <div>
      <ul>
        <!-- Using v-for 2 -->
        <li v-for="car in cars" v-bind:key="car.id">{{ car.year }} {{ car.make }} {{ car.model }}</li> 
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() { 
    return { 
      countProperty: 0, //Click event 1
      showDiv: false, //Conditional Rendering 4
      here: 'here', //Pass Params in Events 3
      cars: [ //Using v-for 1
        { id: 1, make: 'Ford', model: 'Escape', year: 2005 },
        { id: 2, make: 'Ford', model: 'F-250', year: 1999 },
        { id: 3, make: 'Ford', model: 'F-150', year: 2020 },
        { id: 4, make: 'Chevrolet', model: 'Cruze', year: 2005 },
        { id: 5, make: 'Cadillac', model: 'Escalade', year: 2018 },
        { id: 6, make: 'Volkswagon', model: 'Touareg', year: 2005 },
      ]
    }
  },
  methods: {
    thisIsAMethod() {
      this.countProperty -= 1
    }, 
    showAndHideMethod() { //Conditional Rendering 3
      this.showDiv = !this.showDiv 
    }, 
    passParamIntoEvent(event, param) { //Pass Params in Events 2
      console.log(event)
      console.log(param)
      this.here = param
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

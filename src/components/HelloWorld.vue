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
        <!-- Using v-for 2, Attribute Binding 3 (Extra Example using :href), Dynamic Classes 2 using :class. Using key value pairs, the class is being
        evaluated based on if car.isFav is true or false, so it become class="{fav: true}" or false -->
        <li v-for="car in cars" v-bind:key="car.id" :class="{ fav: car.isFav}">{{ car.year }} {{ car.make }} {{ car.model }} | <a :href="car.id">ID Link Attribute Binding</a></li> 
      </ul>
    </div>
    <div>
      <p>Data aka attribute binding</p> <!-- Attribute Binding 1 -->
      <a v-bind:href="aUrl">This comes from aUrl property</a>
      <br>
      <a :href="anotherUrl">This comes from anotherUrl property</a>

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
        { id: 1, make: 'Ford', model: 'Escape', year: 2005, isFav: true }, //Dynamic Classes 1
        { id: 2, make: 'Ford', model: 'F-250', year: 1999, isFav: true  },
        { id: 3, make: 'Ford', model: 'F-150', year: 2020, isFav: true },
        { id: 4, make: 'Chevrolet', model: 'Cruze', year: 2005, isFav: false },
        { id: 5, make: 'Cadillac', model: 'Escalade', year: 2018, isFav: false  },
        { id: 6, make: 'Volkswagon', model: 'Touareg', year: 2005, isFav: false  },
      ],
      aUrl: "www.santamariacode.com", // Attribute Binding 2
      anotherUrl: "www.salvatoresantamaria.com"
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
  li {
    list-style-type: none;
    background: #fff;
    margin: 20px auto;
  }
  /* Dynamic Classes 3 */
  li.fav { 
    color:#ff9ed2; 
  }
</style>

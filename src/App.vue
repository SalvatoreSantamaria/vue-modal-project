<template>

    <div id="app" class="modalcontainer">

      <div v-if="showModal" class="vifshowmodal"> <!--  Emitting Custom event 2 -->
        <Modal theme="sale" thisIsAProp="text data from App.vue" :thisIsADataBoundProp="['an','array',1,2,3]" :dataBoundPropToATemplateProperty="aProperty"
        @close="toggleModal"
        > 
        <!-- 
          Props 1:  Add Attribute. Here attribute (the prop) is called thisIsAProp. 
          Data Binding Props 1: :thisIsADataBoundProp is the prop and bound to an array 
          Data Bound To A Template Prop 1: :dataBoundPropToATemplateProperty is the prop and bound to the template property named aProperty
          // Emitting Custom events 7: Listening to custom event @close, and firing the function "toggleModal"
        -->
        <!-- Named Slots 1. Using slot directive to give template a name, and calling the slot thisIsTheSlotName-->
        <template v-slot:thisIsTheSlotName> 
          <div class="namedslots">
            <a href="#">Named Slot Link 1</a>
            <a href="#">Named Slot Link 2</a>
          </div>
        </template> 

        <!-- Named Slots 1 -->
        <!-- Slots 1 and Slots Default Content 1. If no content, then the default content from the parent <slot></slot>-->
        <h1>Ninja Giveaway</h1>
        <p>Grab your Ninja swag</p>
         <!-- Slots 1-->
        </Modal>
      </div>

      <button @click.right="toggleModal">Open Modal With Right Click</button><!--  Emitting Custom events 3 -->

      <div class="importcomponent">
        <HelloWorld msg="Welcome to Your Vue.js App Yay!"/> <!-- Import component step 2 -->
      </div>
      
      <div class="templateproperty">
        <p>{{ title }}</p> <!--Template Property 2 -->
        <input type="text" ref="templateRef"> <!--Template Ref 1 -->
        <button @click="handleClick">Click</button>
      </div>

      <teleport to=".modals"> <!-- Using Teleport 1 -->
        <div class="usingteleport">
        <h1>This was added using teleport</h1>
        </div>
      </teleport>

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
      aProperty: "This is a text property", //Data Bound To A Template Prop 2: the template data property
      showModal: false //Emitting Custom Events 1
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
    },
    toggleModal() { // Emitting Custom events 4
      this.showModal = !this.showModal
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

.vifshowmodal {
    width: 400px;
    border-radius: 20px;
    background: blue;
    /* color: white; */
    /* text-align: center; */
    padding: 10px 0;
    /* margin: 40px auto; */
}

.modalcontainer {
    width: 400px;
    border-radius: 20px;
    background: #e3f2fd;
    /* color: white; */
    /* text-align: center; */
    padding: 10px 0;
    /* margin: 40px auto; */
}

.namedslots {
    width: 400px;
    border-radius: 20px;
    background: #bbdefb;
    /* color: white; */
    /* text-align: center; */
    padding: 10px 0;
    /* margin: 40px auto; */
}

.importcomponent{
    width: 400px;
    border-radius: 20px;
    background: #90caf9;
    /* color: white; */
    /* text-align: center; */
    padding: 10px 0;
    /* margin: 40px auto; */
}

.templateproperty {
    width: 400px;
    border-radius: 20px;
    background: #64b5f6;
    /* color: white; */
    /* text-align: center; */
    padding: 10px 0;
    /* margin: 40px auto; */
}

.usingteleport {
    width: 400px;
    border-radius: 20px;
    background: #42a5f5;
    /* color: white; */
    /* text-align: center; */
    padding: 10px 0;
    /* margin: 40px auto; */
}



</style>

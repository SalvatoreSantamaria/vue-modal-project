<template>
  <div class="backdrop" @click="closeModal"> <!-- Emitting Custom events 5 -->
    <!-- passing theme prop to add the class 'saleClass' if the theme is equal to sale -->
    <div class="modal" :class="{ saleClass: theme === 'sale' }">
      <p>Modal content</p>
      <p> {{ thisIsAProp }}</p> <!-- Props 3: output the value of the prop onto the page -->
      <p>{{ thisIsADataBoundProp }}</p><!-- Data Bound Props 3: output the value of the prop onto the page -->
      <p>{{ dataBoundPropToATemplateProperty }}</p><!-- Data Bound To A Template Prop 4: output value-->
      <slot></slot>  <!-- Slots 2. This is default and is always called -->
        <div class="actions">
          <!-- Named Slot 2. Must call the slot name -->
            <slot name="thisIsTheSlotName"></slot>
          <!-- Named Slot 2 -->
        </div>
      <slot>This default content text will only show if nothing is passed into the corresponding template</slot><!-- Slots default content 1 -->
    </div>
  </div>
</template>

<script>
export default {
  // props takes in any values we are accepting in this component.
  props: ['theme', 'thisIsAProp', 'thisIsADataBoundProp', 'dataBoundPropToATemplateProperty'],  //Props 2, Data Bound Props 2, Data Bound To A Template Prop 3: Accept prop into child component, should be in quotes
  methods: {
    closeModal() { // Emitting Custom events 6
      this.$emit('close') // this is a custom event
    }
  }
}
</script>


<style>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
    background: purple;
  }
  .modal.saleClass {
    background: crimson;
    color: white;
  }
  .modal.saleClass h1 {
    color: white;
  }
</style>
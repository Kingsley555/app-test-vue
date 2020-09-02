<template>
  <div>
    <number-input :myNum="myNum" @newAdded="newInput" />
  </div>
</template>

<script>
import NumberInput from "./components/NumberInput.vue";

export default {
  name: "App",
  components: {
    NumberInput,
  },

  // sends an array of initial input/data value to the child component
  data() {
    return {
      myNum: [10, 20, 25, 25, 20],
    };
  },

  // Add an input value to existing array of input values
  methods: {
    newInput(numbr) {
      this.myNum.push(numbr);
    },
  },
};
</script>

<style>
</style>

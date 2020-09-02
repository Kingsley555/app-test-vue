
<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h4>{{title}}</h4>
          <hr />
          <div class="form-group text-center" :key="index" v-for="(num, index) in myNum">
            <input type="number" id="num1" class="form-control" v-model.number="myNum[index]" />
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <button class="btn btn-light btn-lg btn-block" @click.prevent="addInput">{{addNum}}</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "NumberInput",
  props: {
    myNum: {
      type: Array,
    },
  },

  data() {
    return {
      title: "AddMe",
      numbr: 0,
    };
  },

  computed: {
    //sums all the in the "myNum array" and the result is displayed on button
    addNum() {
      return this.myNum.reduce((total, num) => {
        return parseInt(total + num);
      });
    },
  },

  methods: {
    // Assigns a random number to numbr
    //emits a "newAdded" event and passes the event and the data to the parent component
    addInput() {
      this.numbr = Math.floor(Math.random() * 10) + 1;
      this.$emit("newAdded", this.numbr);
    },
  },
};
</script>


<style scoped>
h4 {
  text-align: center;
}
input[type="number"] {
  text-align: center;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>

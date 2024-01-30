<template>
  <h1>{{ Title }}</h1>
  <input type="text" v-model="inputValue1" placeholder="Number ..." />
  <br />
  <br />
  <input type="text" v-model="inputValue2" placeholder="Number ..." />
  <br />
  <br />
  <button v-on:click="sortInputValue">Sort</button>
  <button v-on:click="clearInputValue">Clear</button>
  <button v-on:click="changeInputValues">Change</button>
  <br />
</template>
<script>
export default {
  // name, props, data, methods, components, computed
  name: "SecondComponent",
  props: {},
  data() {
    return {
      Title: "Second Component",
      inputValue1: "",
      inputValue2: "",
      tempInputValue: "",
      sortedArray: "",
    };
  },
  methods: {
    compareNumbers(a, b) {
      return a - b;
    },
    sortInputValue() {
      this.sortedArray = [this.inputValue1, this.inputValue2].sort(
        this.compareNumbers
      );
      this.inputValue1 = this.sortedArray[0];
      this.inputValue2 = this.sortedArray[1];
    },
    clearInputValue() {
      this.inputValue1 = this.inputValue2 = "";
    },
    changeInputValues() {
      this.tempInputValue = this.inputValue1;
      this.inputValue1 = this.inputValue2;
      this.inputValue2 = this.tempInputValue;
    },
  },
  components: {},
  computed: {},
};
</script>

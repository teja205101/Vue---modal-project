<template>
  <h1>Hello</h1>

  <h1>{{ title }}</h1>
  <h2>{{ h }}</h2>
  <slot name="one"></slot>
  <br />
  <input type="txt" v-model="numberOne" />
  <input type="txt" v-model="numberTwo" />
  <button @click="Subtraction">Subtract</button>
  {{ sub }}
</template>

<script>
export default {
  // name, props, data, methods, components, computed
  name: "thirdComponent",
  props: ["title", "h"],
  data() {
    return { numberOne: 0, numberTwo: 0, sub: 0 };
  },
  methods: {
    Subtraction() {
      this.sub = parseInt(this.numberOne) - parseInt(this.numberTwo);
    },
  },
};
</script>

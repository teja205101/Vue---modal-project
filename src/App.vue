<template>
  <h1>{{ Title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">Click me</button>
  <p>Welcome ...</p>
  <!-- {{ name }} -->
  <div v-show="showFirstComponent">
    <FirstComponent :array="Array" :greeting="Greeting">
      <template v-slot:one>
        <h1>v-slot:one</h1>
        <a href="#">Sign up now</a>
      </template>

      <template v-slot:third>
        <h1>v-slot:three</h1>
        <a href="#">More Info</a>
      </template>

      <h1>First Component : {{ nonSlotTemplate }}</h1>
      <h2>Hello</h2>
    </FirstComponent>
  </div>

  <div v-if="showModal">
    <Modal>
      <h1>Hello</h1>
      <template v-slot:one> Text passed through v-slot </template>
    </Modal>
  </div>
  <button @click="firstCompnentFlag">{{ messageForButton }}</button>
  <button @click="toggleModal">Show Modal</button>
  <br />
  <button @click="trail">You are cute</button>
  <ThirdComponent title="Third Component" :h="Title">
    <template v-slot:one>
      <h1>Third Component Slot one</h1>
      <h1>Calculator</h1>
      <input type="txt" v-model="numberOne" />
      <input type="txt" v-model="numberTwo" />
      <button @click="add">Add</button>
      {{ sum }}
    </template>
  </ThirdComponent>
  <FourthComponent />
</template>

<script>
import FirstComponent from "./components/FirstComponent";
import ThirdComponent from "./components/ThirdComponent.vue";
import FourthComponent from "./components/FourthComponent.vue";
import Modal from "./components/Modal.vue";

export default {
  // name, props, data, methods, components, computed
  name: "App",
  components: {
    FirstComponent,
    ThirdComponent,
    FourthComponent,
    Modal,
  },
  data() {
    return {
      Title: "My First Data with reactive property name Title",
      nonSlotTemplate:
        "Template's passing  through using Slots without using slots name (v-slot)",
      Array: ["Teja", "Vishal", "Lokesh"],
      showFirstComponent: true,
      messageForButton: "Hide First Component",
      Greeting: "",
      showModal: false,
      numberOne: 0,
      numberTwo: 0,
      sum: 0,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    firstCompnentFlag() {
      this.showFirstComponent = !this.showFirstComponent;
      if (!this.showFirstComponent) {
        this.messageForButton = "Show First Component";
      } else {
        this.messageForButton = "Hide First Component";
      }
    },
    trail() {
      console.log(this.Greeting);
      if (this.Greeting === "Hello") {
        this.Greeting = "";
      } else {
        this.Greeting = "Hello";
      }
    },
    toggleModal() {
      console.log("show modal");
      this.showModal = !this.showModal;
    },
    add() {
      this.sum = parseInt(this.numberOne) + parseInt(this.numberTwo);
    },
  },
};
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
h1 {
  color: red;
  background-color: black;
}
</style>

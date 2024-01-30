<template>
  <h1>Hello</h1>
  <slot name="one">default content</slot>
  <slot>default content</slot>
  <slot name="third">default content</slot>
  <ul>
    <li
      v-for="i in array"
      :key="i"
      :class="{
        one: i === 'Teja',
        two: i === 'Vishal',
        three: i === 'Lokesh',
      }"
    >
      {{ greeting }} {{ i }}
    </li>
  </ul>
  <ol>
    <li
      v-for="i in ar"
      :key="i"
      :class="{
        one: i === 'Teja',
        two: i === 'Vishal',
        three: i === 'Lokesh',
      }"
    >
      {{ i }}
    </li>
  </ol>
  <SecondComponent />
  <div class="aParent">
    <div>
      <v-select>
        <option v-for="item in arA" :key="item" @click="selectedItems">
          {{ item }}
        </option>
      </v-select>
    </div>
    <button @click="rightTransfer">Right Transfer</button>
    <button @click="leftTransfer">Left Transfer</button>
    <div>
      <v-select>
        <option v-for="item in arB" :key="item" @click="selectedItems">
          {{ item }}
        </option>
      </v-select>
    </div>
  </div>
</template>

<script>
import SecondComponent from "./SecondComponent.vue";

export default {
  //name, props, data, methods, components, computed
  name: "FirstComponent",
  props: ["array", "greeting"],
  data() {
    return {
      arA: ["Teja", "Lokesh", "Shiva"],
      arB: ["Shalini", "vamsi", "Mani"],
      selectedItem: [],
      indexA: "",
      indexB: "",
    };
  },
  methods: {
    selectedItems(e) {
      if (!this.selectedItem.includes(e.target.innerText)) {
        this.selectedItem.push(e.target.innerText);
      }
      console.log(this.selectedItem.includes(e.target.innerText));
    },
    rightTransferFunction(item) {
      if (!this.arB.includes(item)) {
        this.arB.push(item);
        this.indexA = this.arA.indexOf(item);
        this.arA.splice(this.indexA, 1);
      }
    },
    rightTransfer() {
      this.selectedItem.forEach(this.rightTransferFunction);
      this.selectedItem = [];
    },
    leftTransferFunction(item) {
      if (!this.arA.includes(item)) {
        this.arA.push(item);
        this.indexB = this.arB.indexOf(item);
        this.arB.splice(this.indexB, 1);
      }
    },
    leftTransfer() {
      this.selectedItem.forEach(this.leftTransferFunction);
      this.selectedItem = [];
    },
  },
  computed: {},
  components: { SecondComponent },
};
</script>

<style scoped>
h1 {
  color: yellow;
}
.one {
  color: red;
}
.two {
  color: orange;
}
.three {
  color: aqua;
}
.aParent div {
  padding-left: 200px;
  display: inline-block;
}

button {
  margin: 0px 50px;
}
</style>

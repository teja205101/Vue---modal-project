<template>
  <div class="backdrop">
    <div class="modal">
      <slot></slot>
      <slot name="one"></slot>
      <p>Modal contant</p>
    </div>
  </div>
</template>
<script>
export default {
  name: "firstModal",
};
</script>
<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
  z-index: 1001;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
  z-index: 1000;
}
</style>

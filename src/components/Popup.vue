<template>
  <div class="popup_mask">
    <div class="popup_content">
      <slot name="title" :data="userTitle"></slot>
      <slot name="content" :data="userContent"></slot>
      <div class="x_icon" @click="closePopup"></div>
      <button @click="add">+</button>
    </div>
  </div>
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  name: "Popup",
  props: {
    userTitle: {
      type: String,
      default: () => "",
    },
    userContent: {
      type: String,
      default: () => "",
    },
  },
  methods: {
    closePopup() {
      this.$emit("close");
    },
    add() {
      this.$emit("add");
    },
  },
});
</script>

<style lang="scss" scoped>
* {
  box-sizing: border-box;
}
.popup_mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #333a;
  z-index: 999;
  .popup_content {
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    margin: auto;
    height: 300px;
    width: 300px;
    background-color: #fff;
    .x_icon {
      position: absolute;
      z-index: 1000;
      top: -8px;
      right: -8px;
      cursor: pointer;
      padding: 4px;
      width: 24px;
      height: 24px;
      background-color: #ccc;
      border-radius: 50%;
      display: grid;
      place-items: center;
      &::before,
      &::after {
        content: "";
        grid-row: 1/1;
        grid-column: 1/1;
        height: 2px;
        width: 12px;
        background-color: #222;
        transform: rotate(45deg);
      }
      &::after {
        transform: rotate(-45deg);
      }
    }
  }
}
</style>

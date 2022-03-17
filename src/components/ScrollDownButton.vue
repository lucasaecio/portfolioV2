<template>
  <button class="scrollDown" @click="buttonClick">
    <span class="scrollDown__arrow"></span>{{ label }}
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ScrollDownButton",
  props: ["label"],
  methods: {
    buttonClick() {
      this.$emit("scroll-down-click");
    },
  },
});
</script>

<style scoped>
.scrollDown {
  position: absolute;
  bottom: 0;
  left: calc(50% - 50px);
  z-index: 2;
  width: 100px;
  display: inline-block;
  transform: translate(0, -40%);
  color: #fff;
  font-family: Roboto, sans-serif;
  font-size: 20px;
  letter-spacing: 0.1em;
  text-decoration: none;
  transition: opacity 0.3s;
  padding: 70px 0 0 0;
  background-color: transparent;
  border: none;
  cursor: pointer;
  white-space: nowrap;
}
.scrollDown:hover {
  opacity: 0.5;
}

.scrollDown .scrollDown__arrow {
  position: absolute;
  top: 0;
  left: calc(50% - 12px);
  width: 24px;
  height: 24px;
  border-left: 1px solid #fff;
  border-bottom: 1px solid #fff;
  transform: rotate(-45deg);
  animation: sdb05 1.5s infinite;
  box-sizing: border-box;
}
@-webkit-keyframes sdb05 {
  0% {
    transform: rotate(-45deg) translate(0, 0);
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    transform: rotate(-45deg) translate(-20px, 20px);
    opacity: 0;
  }
}
@keyframes sdb05 {
  0% {
    transform: rotate(-45deg) translate(0, 0);
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    transform: rotate(-45deg) translate(-20px, 20px);
    opacity: 0;
  }
}
</style>

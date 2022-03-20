<template>
  <div class="progress" :style="{ width: width }">
    <div class="progress-value" :style="{ width: percent }"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ProgressBar",
  props: ["width", "percent"],
});
</script>

<style scoped>
.progress {
  background: rgba(255, 255, 255, 0.1);
  justify-content: flex-start;
  border-radius: 100px;
  align-items: center;
  position: relative;
  padding: 0 5px;
  display: flex;
  height: 16px;
}

.progress-value {
  box-shadow: 0 2px 20px -3px #fff;
  border-radius: 100px;
  background: #9257ff;
  height: 8px;
}
</style>

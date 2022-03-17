<template>
  <main :class="{ 'app-section': !hasDataLoaded }">
    <MainPage v-if="hasDataLoaded"></MainPage>
    <LoaderComponent v-else></LoaderComponent>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import LoaderComponent from "./components/LoaderComponent.vue";
import MainPage from "./views/MainPage.vue";

export default defineComponent({
  name: "App",
  components: {
    LoaderComponent,
    MainPage,
  },
  data() {
    return {
      userData: {},
      hasDataLoaded: false,
    };
  },
  created() {
    fetch("https://api.jsonbin.io/b/62241b4f06182767436e0ff4/2")
      .then((T) => T.json())
      .then((response) => {
        this.userData = response;
        this.hasDataLoaded = true;
      });
  },
});
</script>

<style>
:root {
  --main-bg-color: #191920;
  --color-purple: #e613f1;
}

.app-section {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>

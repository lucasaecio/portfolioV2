<template>
  <section class="main">
    <section class="presentation" id="presentation">
      <div>
        <h1 class="presentation__title">
          Olá, <span class="presentation__icon">&#128075;</span>
          <span class="presentation__title-animation"></span>
        </h1>
        <h1 class="presentation__title">
          Me chamo <span class="presentation__title-animation"></span>
        </h1>
        <h1 class="presentation__title">
          Lucas Aécio <span class="presentation__title-animation"></span>
        </h1>
      </div>

      <ScrollDownButton
        @scroll-down-click="scrollTo('aboutme')"
        :label="'About Me'"
      />
    </section>

    <section class="aboutme" id="aboutme">teste</section>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import $ from "jquery";
import ScrollDownButton from "@/components/ScrollDownButton.vue";

export default defineComponent({
  name: "MainPage",
  data() {
    return {};
  },
  components: { ScrollDownButton },
  methods: {
    scrollTo(sectionID = "presentation") {
      let sectionData = $(`#${sectionID}`).offset() ?? { top: 0 };

      $("html, body").animate({ scrollTop: sectionData.top }, 500, "linear");
    },
  },
});
</script>

<style scoped>
.presentation {
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
  flex-direction: row;
}
.presentation::before {
  text-align: start;
  content: " ";
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  opacity: 0.3;
  background-image: url("@/assets/img/background.jpg");
  background-repeat: no-repeat;
  background-position: 0 77%;
  background-size: cover;
}

.presentation .presentation__title {
  z-index: 2;
  display: block;
  width: fit-content;
  font-size: 4.3rem;
  font-weight: 700;
  position: relative;
  color: transparent;
  animation: presentation_title 0.5s ease forwards 1s;
  animation-delay: 1s;
}
.presentation .presentation__title:nth-child(3) {
  animation: my_name 0.5s ease forwards 1s;
}

.presentation .presentation__title .presentation__title-animation {
  animation-delay: 0.5;
}

.presentation .presentation__title .presentation__title-animation {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 0;
  background-color: var(--color-purple);
  animation-name: span_text;
  animation-duration: 1s;
  animation-timing-function: ease;
  animation-delay: 0.5s;
}

.presentation .presentation__icon {
  display: inline-block;
  animation-name: presention_icon;
  animation-duration: 1.5s;
  animation-timing-function: linear;
  animation-delay: 2s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}

.aboutme {
  height: 100vh;
}

/* ANIMATION */
@keyframes presention_icon {
  0% {
    transform: rotateZ(0deg);
  }
  100% {
    transform: rotateZ(15deg);
  }
}

@keyframes span_text {
  50% {
    width: 100%;
    left: 0;
  }
  100% {
    width: 0;
    left: 100%;
  }
}
@keyframes presentation_title {
  100% {
    color: white;
  }
}

@keyframes my_name {
  100% {
    color: var(--color-purple);
  }
}
</style>

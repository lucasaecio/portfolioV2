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

    <section class="aboutme" id="aboutme">
      <div class="aboutme__section">
        <div class="aboutme__header">
          <h1 class="aboutme__title">About Me</h1>
        </div>
        <div class="aboutme__main">
          <img class="image" src="@/assets/img/profile.jpg" />

          <div class="card">
            <div class="card__text">
              <p>
                É um prazer em tê-lo por aqui, me chamo Lucas, sou Desenvolvedor
                Fullstack, atualmente moro em Recife - Pernambuco. No meu tempo
                livre, tenho alguns hobbies, amo viajar de moto e além disso
                também amo música até mesmo toco alguns instrumentos musicais.
              </p>
            </div>
            <div class="card__graphs">
              <div class="graphs__item">
                <span>Vue</span>
                <ProgressBar width="100%" percent="75%" />
              </div>
              <div class="graphs__item">
                <span>ReactJS</span>
                <ProgressBar width="100%" percent="45%" />
              </div>
              <div class="graphs__item">
                <span>CSS</span>
                <ProgressBar width="100%" percent="80%" />
              </div>
              <div class="graphs__item">
                <span>Typescript</span>
                <ProgressBar width="100%" percent="40%" />
              </div>
              <div class="graphs__item">
                <span>Javascript</span>
                <ProgressBar width="100%" percent="80%" />
              </div>
              <div class="graphs__item">
                <span>PHP</span>
                <ProgressBar width="100%" percent="70%" />
              </div>
              <div class="graphs__item">
                <span>Node</span>
                <ProgressBar width="100%" percent="50%" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import $ from "jquery";
import ScrollDownButton from "@/components/ScrollDownButton.vue";
import ProgressBar from "@/components/ProgressBar.vue";

export default defineComponent({
  name: "MainPage",
  data() {
    return {};
  },
  components: { ScrollDownButton, ProgressBar },
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

/* ABOUT ME */

.aboutme {
  height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.aboutme__section {
  max-width: 50%;
  margin-top: 150px;
}
.aboutme__header {
  margin-bottom: 60px;
}
.aboutme__title {
  font-size: 2.5em;
}
.aboutme__main {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.aboutme__main .image {
  height: 170px;
  width: 170px;
  border-radius: 50%;
  object-fit: cover;
  object-position: 100% 37%;
}

.aboutme__main .card {
  max-width: 73%;
  background-color: #2f2f2f;
  padding: 25px;
  border-radius: 25px;

  display: flex;
}
.aboutme__main .card__text {
  flex: 2;
  line-height: 23px;
  max-width: 55%;
  margin-right: 30px;
  text-align: justify;
}

.aboutme__main .card__graphs {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.aboutme__main .card__graphs .graphs__item {
  margin-bottom: 12px;
}

.aboutme__main .card__graphs .graphs__item:last-child {
  margin-bottom: 0px;
}
</style>

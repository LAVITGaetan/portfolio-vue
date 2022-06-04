<template>
  <div id="app">
    <div id="grid">
  <Content v-if="contentArray[0] == undefined"/>
  <Presentation :msg="messagez" v-if="contentArray[0] === 'Presentation'"/>
  <Project :msg="message" v-if="contentArray[0] === 'Project'"/>
  <Competence :msg="messagea" v-if="contentArray[0] === 'Competence'"/>
      <div class="nav nav1" @click="nav('Presentation')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Présentation</h2>
      </div>
      <div class="nav nav2" @click="nav('Project')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Projets</h2>
      </div>
      <div class="nav nav3" @click="nav('Competence')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Compétences</h2>
      </div>
    </div>
  </div>
</template>

<script>

import Content from './components/Content.vue';
import Presentation from './components/Project.vue';
import Project from './components/Project.vue';
import Competence from './components/Project.vue';

export default {
  name: "App",
  components: {
    Content,
    Presentation,
    Project,
    Competence
  },
  data () {
    return {
      message:'hi',
      messagez:'hizzz',
      messagea:'hiaaaa',
      contentArray:[]
    }
  },
  methods: {
    nav(content) {
      this.contentArray = [];
      this.contentArray.push(content)
    }
  }
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

@font-face {
  font-family: Raleway;
  src: url(./fonts/Raleway.ttf);
}

:root {
  --colorCta: #65fbd2;
  --colorCtaLighter: #80f2d4;
  --colorCtaDarker: #48dfb7;
  --filterCta: brightness(0) saturate(100%) invert(79%) sepia(37%)
    saturate(568%) hue-rotate(102deg) brightness(108%) contrast(97%);
  --colorDark: #0b192f;
  --colorDarkLighter: #101e34;
  --colorLight: #e3f0ff;
  --colorLightLighter: #bdccde;
}

#app {
  width: 100vw;
  height: 100vh;
  background: var(--colorDark);
  font-family: Raleway;
}

#grid {
  width: 100vw;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(3, 3fr) 2fr 1fr;
  grid-template-rows: repeat(5, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

.color0 nav-icon {
  filter: var(--filterCta);
}

.nav {
  display: flex;
  align-items: center;
  padding: 0 10%;
  position: relative;
  cursor: pointer;
}

.nav::before {
  transition: 0.3s ease-out;
  content: "";
  position: absolute;
  background: var(--colorDarkLighter);
  width: 0%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 10;
}

.nav:hover:before {
  transition: 0.3s ease-in;
  width: 100%;
}

.nav::after {
  transition: 0.3s ease-out;
  content: "";
  position: absolute;
  background: var(--colorLight);
  width: 0%;
  height: 0%;
  clip-path: polygon(50% 0%, 23% 51%, 50% 100%, 0% 50%);
  top: calc(50% - 12px);
  right: 100px;
  z-index: 50;
}

.nav:hover:after {
  transition: 0.3s ease-in;
  width: 24px;
  height: 24px;
  right: 15px;
}

.nav:hover {
  transition-delay: 0.3s;
  box-shadow: 5px 5px 10px #00000050;
}

.nav:hover .nav-title {
  transition: 0.3s ease-in;
  color: var(--colorLight);
  letter-spacing: 0.15em;
}

.nav1 {
  transition: 0.3s ease-out;
  grid-area: 2 / 1 / 2 / 2;
}

.nav2 {
  transition: 0.3s ease-out;
  grid-area: 3 / 1 / 4 / 2;
}

.nav3 {
  transition: 0.3s ease-out;
  grid-area: 4 / 1 / 4 / 2;
}

.nav-icon {
  z-index: 100;
}

.nav-title {
  transition: 0.3s ease-out;
  font-size: 18px;
  color: var(--colorLightLighter);
  font-size: 600;
  padding-left: 20px;
  letter-spacing: 0.1em;
  z-index: 100;
}

#content, #presentation, #project, #competence {
  grid-area: 2 / 2 / 6 / 6;
  background: var(--colorDarkLighter);
}
</style>

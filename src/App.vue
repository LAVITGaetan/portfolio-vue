<template>
    <div id="grid">
      <Content v-if="contentArray[0] == undefined" />
      <Presentation v-if="contentArray[0] === 'presentation'" />
      <Project v-if="contentArray[0] === 'project'" />
      <Competence v-if="contentArray[0] === 'competence'" />
      <Contact v-if="contentArray[0] === 'contact'" />
      <div id="hero"><h1 class="hero-title color0"></h1></div>
      <div class="nav" id="nav-presentation" @click="nav('presentation')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Présentation</h2>
      </div>
      <div class="nav" id="nav-project" @click="nav('project')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Projets</h2>
      </div>
      <div class="nav" id="nav-competence" @click="nav('competence')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Compétences</h2>
      </div>
            <div class="nav" id="nav-contact" @click="nav('contact')">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Me contacter</h2>
      </div>
      <div id="nav-theme">
        <img class="theme-icon" src="./assets/theme-green.svg" />
        <img class="theme-icon" src="./assets/theme-yellow.svg" />
        <img class="theme-icon" src="./assets/theme-purple.svg" />
      </div>
    </div>
</template>

<script>
import Content from "./components/Content.vue";
import Presentation from "./components/Presentation.vue";
import Project from "./components/Project.vue";
import Competence from "./components/Competence.vue";
import Contact from "./components/Contact.vue";
export default {
  name: "App",
  components: {
    Content,
    Presentation,
    Project,
    Competence,
    Contact
  },
  data() {
    return {
      contentArray: [],
    };
  },
  methods: {
    navDesign(content) {
      setTimeout(() => {
        // remove active class from every nav items
        let presentation = document.getElementById("nav-presentation");
        let project = document.getElementById("nav-project");
        let competence = document.getElementById("nav-competence");
        let contact = document.getElementById("nav-contact");
        presentation.classList.remove("nav-active");
        project.classList.remove("nav-active");
        competence.classList.remove("nav-active");
        contact.classList.remove("nav-active");

        // add active class to target element
        let element = document.getElementById(`nav-${content}`);
        element.classList.add("nav-active");
      }, 100);
    },
    nav(content) {
      // Display content from the selected nav item
      this.contentArray = [];
      this.contentArray.push(content);

      // A css function to style the selected nav item
      this.navDesign(content);
    },
  },
};
</script>

<style>
/* Global settings*/
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

/* /Global settings/ */
/* Grid */
#grid {
  width: 100vw;
  height: 100vh;
  display: grid;
  grid-template-columns: repeat(3, 3fr) 2fr 1fr;
  grid-template-rows: repeat(5, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

#hero {
  grid-area: 1 / 1 / 1 / 2;
  background-color: var(--colorDark);
  background-image: url(./assets/design.png);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  margin: 30px;
  border-radius: 3px;
}

.color0 {
  filter: var(--filterCta);
}

.nav {
  display: flex;
  align-items: center;
  padding: 0 10%;
  position: relative;
  cursor: pointer;
}

.nav-active {
  background: var(--colorDarkLighter);
  box-shadow: 5px 5px 10px #00000020;
  margin: 20px;
  border-left: 3px solid var(--colorCta);
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

#nav-presentation {
  transition: 0.3s ease-out;
  grid-area: 1 / 1 / 1 / 2;
}

#nav-project {
  transition: 0.3s ease-out;
  grid-area: 2 / 1 / 2 / 2;
}

#nav-competence {
  transition: 0.3s ease-out;
  grid-area: 3 / 1 / 3 / 2;
}

#nav-contact {
  transition: 0.3s ease-out;
  grid-area: 4 / 1 / 4 / 2;
}


#nav-theme {
  transition: 0.3s ease-out;
  grid-area: 5 / 1 / 5 / 2;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
}

.theme-icon {
  width: 64px;
  cursor: pointer;
  height: 64px;
}

.nav-icon {
  z-index: 100;
  width: 24px;
  height: 24px;
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

#content,
#presentation,
#project,
#competence,
#contact {
  grid-area: 1 / 2 / 6 / 6;
  background: var(--colorDark);
  border-top-left-radius: 5px;
  padding: 15px;
  margin: 25px;
  border-left: 10px double var(--colorDarkLighter);
}

</style>

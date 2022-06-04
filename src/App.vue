<template>
  <div id="app">
    <div id="grid">
      <div class="settings">
        <img
          src="./assets/outlined-settings.svg"
          width="48px"
          height="48px"
          class="color0 nav-icon"
        />
      </div>
      <div class="nav nav1">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Présentation</h2>
      </div>
      <div class="nav nav2">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Projets</h2>
      </div>
      <div class="nav nav3">
        <img
          class="color0 nav-icon"
          src="./assets/polygon-full.svg"
          width="48px"
          height="48px"
        />
        <h2 class="nav-title">Compétences</h2>
      </div>
      <div class="content"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
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
  --filterCta: brightness(0) saturate(100%) invert(79%) sepia(37%)
    saturate(568%) hue-rotate(102deg) brightness(108%) contrast(97%);
  --colorDark: #0b192f;
  --colorDarkLighter: #101e34;
  --colorLight: #e3f0ff;
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
  grid-template-rows: repeat(6, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

.settings {
  transition: 0.3s ease-out;
  grid-area: 1 / 5 / 2 / 6;
  background: var(--colorDarkLighter);
  display: flex;
  align-items: center;
  box-shadow: 5px 5px 10px #00000050;
  justify-content: center;
  position: relative;
}

.settings:before {
  transition: 0.5s ease-in;
  content: "";
  position: absolute;
  width: 0%;
  height: 100%;
  background: var(--colorDarkLighter);
  box-shadow: 5px 5px 10px #00000020;
  right: 0;
  top: 0;
}

.settings:hover {
  transition: 0.3s ease-in;
  cursor: pointer;
  box-shadow: 5px 5px 10px #00000000;
}

.settings:hover:before {
  box-shadow: 5px 5px 10px #00000050;
  width: 300%;
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
  right: 0;
}

.nav:hover {
  transition-delay: 0.3s;
  box-shadow: 5px 5px 10px #00000050;
}

.nav:hover .nav-title {
  transition: 0.3s ease-in;
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
  color: var(--colorLight);
  font-size: 600;
  padding-left: 25px;
  letter-spacing: 0.1em;
  z-index: 100;
}

.content {
  grid-area: 2 / 2 / 7 / 6;
}
</style>

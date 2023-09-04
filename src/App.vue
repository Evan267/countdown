<template>
  <Countdown id="countdown"></Countdown>
</template>

<script>
import Countdown from "./components/Countdown.vue"

export default {
  components: {
    Countdown
  }
}
</script>

<style>
p, body {
  margin: 0;
}

h1, h2, h3, h4, h5, h6 {
  font-family: "Handlee";
}

#app {
  height: 100vh;
  width: 100vw;
  position: absolute;
  overflow: hidden;
}

#app::before {
  content: "";
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  width: 50vw;
  height: 100vh;
  background-color: #E67DB4A0;
  transition: transform 700ms;
}

#app::after {
  content: "";
  display: block;
  position: absolute;
  top: 0;
  right: 0;
  width: 50vw;
  height: 100vh;
  background-color: #5AC3F5A0;
  transition: transform 500ms;
}

#app.none::after {
  transform: translateX(100%);
}

#app.none::before {
  transform: translateX(-100%);
}

#countdown {
  position: absolute;
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>

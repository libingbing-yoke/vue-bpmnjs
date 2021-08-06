<template>
  <div id="nav">
    <basic></basic>
  </div>
</template>

<script>
import basic from "./components/basic.vue";
export default {
  components: {
    basic,
  },
};
</script>

<style>
html,
body {
  width: 100vw;
  height: 100vh;
  margin: 0;
}

#app,
#nav {
  width: 100vh;
  height: 100vw;
}
</style>
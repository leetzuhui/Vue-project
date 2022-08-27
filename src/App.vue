<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <h1 class="title">Created by TZUHUI</h1>
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  methods: {
    UnusedHandler() { },
  },
};
</script>

<style lang="scss">
#app {
  text-align: center;
  margin-top: 60px;
}
</style>

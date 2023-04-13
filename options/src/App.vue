<template>
  <Home first-name="Developer" last-name="Vue"></Home>
</template>

<script>
    import Home from "./components/Home.vue";
    import { provide, ref } from "vue";

    export default {
        name: "App",
        components: {
            Home,
        },
        setup() {
          const username = ref("developuser")
          provide("username", username);
        },
    };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
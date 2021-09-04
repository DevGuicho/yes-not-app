<template>
  <Indecision />
  <!-- <Counter /> -->
</template>

<script>
//import Counter from "@/components/Counter.vue";
import Indecision from "./Indecision.vue";

export default {
  name: "App",
  components: {
    Indecision,
    //Counter,
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

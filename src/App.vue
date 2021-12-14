<template>
  <div id="app">
    <CityAndDistrict v-model="value" />
    {{ value }}
  </div>
</template>

<script>
  import CityAndDistrict from "./components/CityAndDistrict";

  export default {
    name: "App",
    components: {
      CityAndDistrict,
    },
    data() {
      return {
        value: null,
      };
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

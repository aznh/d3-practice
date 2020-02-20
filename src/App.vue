<template>
  <div id="app">
    <FirstExample/>
    <ArrayExample/>
    <HelloWorldD3/>
    <HelloWorldCircle/>
    <InlineFunctionDataAccess/>
    <Cities/>
  </div>
</template>

<script>
  import FirstExample from "./components/FirstExample"
  import ArrayExample from "./components/ArrayExample";
  import HelloWorldD3 from "./components/HelloWorldD3";
  import HelloWorldCircle from "./components/HelloWorldCircle";
  import InlineFunctionDataAccess from "./components/InlineFunctionDataAccess";
  import Cities from "./components/Cities";

  export default {
    name: 'app',
    components: {
      Cities,
      InlineFunctionDataAccess,
      HelloWorldCircle,
      HelloWorldD3,
      ArrayExample,
      FirstExample,
    }
  }
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>

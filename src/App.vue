<template>
  <div id="app">
<!--    <FirstExample/>-->
<!--    <ArrayExample/>-->
<!--    <HelloWorldD3/>-->
<!--    <HelloWorldCircle/>-->
<!--    <InlineFunctionDataAccess/>-->
<!--    <Cities/>-->
<!--    <ChartExample/>-->
<!--    <BoxPlotExample/>-->
<!--    <LineGraphExample/>-->
<!--    <RoastingGraphExample/>-->
    <BarGraphExample/>
    <HorizontalBarGraphExample/>
  </div>
</template>

<script>
  import FirstExample from "./components/FirstExample"
  import ArrayExample from "./components/ArrayExample";
  import HelloWorldD3 from "./components/HelloWorldD3";
  import HelloWorldCircle from "./components/HelloWorldCircle";
  import InlineFunctionDataAccess from "./components/InlineFunctionDataAccess";
  import Cities from "./components/Cities";
  import ChartExample from "./components/ChartExample";
  import BoxPlotExample from "./components/BoxPlotExample";
  import LineGraphExample from "./components/LineGraphExample";
  // import RoastingGraphExample from "./components/RoastingGraphExample";
  import BarGraphExample from "./components/BarGraphExample";
  import HorizontalBarGraphExample from "./components/HorizontalBarGraphExample";

  export default {
    name: 'app',
    components: {
      HorizontalBarGraphExample,
      BarGraphExample,
      // RoastingGraphExample,
      LineGraphExample,
      BoxPlotExample,
      ChartExample,
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

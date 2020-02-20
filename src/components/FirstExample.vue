<template>
  <div id="borderdiv">
  </div>
</template>

<script>
import * as d3 from "d3";

export default {
  name: 'FirstExample',
  data() {
    return {
      someData: [
        "filler",
        "filler",
        "filler",
        "filler",
      ]
    }
  },
  mounted() {
    d3.select("body")
      .selectAll("div#borderdiv")
      .data(this.someData)
      .enter()
      .append("div")
      .html("Wow")
      .append("span")
      .html("Even More Wow")
      .style("font-weight", "900");
  }
}
</script>

<style>
  #borderdiv {
    width: 200px;
    height: 50px;
    border: 1px solid black;
  }
</style>

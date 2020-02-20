<template>
  <svg ref="helloWorldCircleTarget" style="width:500px;height:500px;border:1px lightgray solid;"></svg>
</template>

<script>
  import * as d3 from "d3";

  export default {
    name: "HelloWorldCircle",
    mounted() {
      // d3.select("svg")
      //   .append("line")
      //   .attr("x1", 20)
      //   .attr("y1", 20)
      //   .attr("x2", 400)
      //   .attr("y2", 400)
      //   .style("stroke", "black")
      //   .style("stroke-width", "2px");
      //
      // d3.select("svg")
      //   .append("text")
      //   .attr("x", 20)
      //   .attr("y", 20)
      //   .text("HELLO");
      //
      // d3.select("svg")
      //   .append("circle")
      //   .attr("r", 20)
      //   .attr("cx", 20)
      //   .attr("cy", 20)
      //   .style("fill", "red");
      //
      // d3.select("svg")
      //   .append("circle")
      //   .attr("r", 100)
      //   .attr("cx", 400)
      //   .attr("cy", 400)
      //   .style("fill", "lightblue");
      //
      // d3.select("svg")
      //   .append("text")
      //   .attr("x", 400)
      //   .attr("y", 400)
      //   .text("WORLD");

      d3.select(this.$refs.helloWorldCircleTarget)
        .append("circle")
        .attr("r", 20)
        .attr("cx", 20)
        .attr("cy", 20)
        .style("fill", "red");

      d3.select(this.$refs.helloWorldCircleTarget)
        .append("text")
        .attr("id", "a")
        .attr("x", 20)
        .attr("y", 20)
        .style("opacity", 0)
        .text("HELLO WORLD");

      d3.select(this.$refs.helloWorldCircleTarget)
        .append("circle")
        .attr("r", 100)
        .attr("cx", 400)
        .attr("cy", 400)
        .style("fill", "lightblue");

      d3.select(this.$refs.helloWorldCircleTarget)
        .append("text")
        .attr("id", "b")
        .attr("x", 400)
        .attr("y", 400)
        .style("opacity", 0)
        .text("Uh, hi.");

      setTimeout(() => {
        d3.select("#a").transition().delay(1000).style("opacity", 1);
        d3.select("#b").transition().delay(1000).style("opacity", 0.75);
        d3.select(this.$refs.helloWorldCircleTarget).selectAll("circle").transition().duration(2000).attr("cy", 200);
      }, 1000)
    }
  }
</script>

<style scoped>

</style>

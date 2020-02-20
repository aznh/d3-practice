<template>
  <svg ref="inlineFunctionDataAccessTarget"></svg>
</template>

<script>
  import * as d3 from "d3"

  export default {
    name: "InlineFunctionDataAccess",
    mounted() {
      // const yScale = d3.scaleLinear().domain([0, 24500]).range([0, 100]);
      // const yScale = d3.scaleLinear().domain([0, 100, 1000, 24500]).range([0, 50, 75, 100]);
      const yScale = d3.scaleLinear().domain([0, 100, 500]).range([0, 50, 100]).clamp(true);
      // const yScale = d3.scaleLinear().domain([0, 100, 500]).range([0, 50, 100]);

      d3.select(this.$refs.inlineFunctionDataAccessTarget)
        .selectAll("rect")
        .data([14, 68, 24500, 430, 19, 1000, 5555])
        .enter()
        .append("rect")
        .attr("width", 10)
        .attr("height", d => yScale(d))
        .style("fill", "blue")
        .style("stroke", "red")
        .style("stroke-width", "1px")
        .style("opacity", .25)
        .attr("x", (d, i) => i * 10)
        .attr("y", d => (100 - yScale(d)))
    }
  }
</script>

<style scoped>

</style>

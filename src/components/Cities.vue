<template>
  <svg ref="cities"></svg>
</template>

<script>
  import * as d3 from "d3";

  let data = `"label","population","country","x","y"
"San Francisco", 750000,"USA",37,-122
"Fresno", 500000,"USA",36,-119
"Lahore",12500000,"Pakistan",31,74
"Karachi",13000000,"Pakistan",24,67
"Rome",2500000,"Italy",41,12
"Naples",1000000,"Italy",40,14
"Rio",12300000,"Brazil",-22,-43
"Sao Paolo",12300000,"Brazil",-23,-46`;

  export default {
    name: "Cities",
    async mounted() {
      let result = await d3.csvParse(data);
      this.dataViz(result);
    },
    methods: {
      dataViz (incomingData) {
        const maxPopulation = d3.max(incomingData, (el) => {
          return parseInt(el.population);
        });

        const yScale = d3.scaleLinear()
          .domain([0, maxPopulation])
          .range([0, 460]);

        d3.select(this.$refs.cities).attr("style", "height: 480px; width: 600px;");
        d3.select(this.$refs.cities).selectAll("rect")
          .data(incomingData)
          .enter()
          .append("rect")
          .attr("width", 50)
          .attr("height", d => yScale(parseInt(d.population)))
          .attr("x", (d, i) => i * 60)
          .attr("y", d => (480 - yScale(parseInt(d.population))))
          .style("fill", "blue")
          .style("stroke", "red")
          .style("stroke-width", "1px")
          .style("opacity", .25);
      }
    }
  }
</script>

<style scoped>

</style>

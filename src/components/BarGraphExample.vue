<template>
  <div ref="barGraph"></div>
</template>

<script>
  import * as d3 from "d3";

  const origin = `Country,Value
United States,12394
Russia,6148
Germany (FRG),1653
France,2162
United Kingdom,1214
China,1131
Spain,814
Netherlands,1167
Italy,660
Israel,1263`

  export default {
    name: "BarGraphExample",
    async mounted() {
      const barEl = this.$refs.barGraph;

      const margin = {top: 30, right: 30, bottom: 70, left: 60},
        width = 460 - margin.left - margin.right,
        height = 400 - margin.top - margin.bottom;

      const svg = d3.select(barEl)
        .append("svg")
        .attr("width", width + margin.left + margin.right)
        .attr("height", height + margin.top + margin.bottom)
        .append("g")
        .attr("transform", "translate(" + margin.left + "," + margin.top + ")");

      const data = await d3.csvParse(origin);
      const x = d3.scaleBand()
        .range([0, width])
        .domain(data.map(d => d.Country))
        .padding(0.2);

      svg.append("g")
        .attr("transform", "translate(0," + height + ")")
        .call(d3.axisBottom(x));

      const y = d3.scaleLinear()
        .domain([0, 13000])
        .range([height, 0]);

      svg.append("g")
        .call(d3.axisLeft(y));

      svg.selectAll("mybar")
        .data(data)
        .enter()
        .append("rect")
        .attr("x", d => x(d.Country))
        .attr("y", d => y(d.Value))
        .attr("width", x.bandwidth())
        .attr("height", d => (height - y(d.Value)))
        .attr("fill", "#69b3a2");

    }
  }
</script>

<style scoped>

</style>

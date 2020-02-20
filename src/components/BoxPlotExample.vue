<template>
  <svg style="width: 800px; height: 800px;" ref="boxPlotTarget"></svg>
</template>

<script>
  import * as d3 from "d3";
  const data = `day,min,max,median,q1,q3,number
1,14,65,33,20,35,22
2,25,73,25,25,30,170
3,15,40,25,17,28,185
4,18,55,33,28,42,135
5,14,66,35,22,45,150
6,22,70,34,28,42,170
7,14,65,33,30,50,28`

  export default {
    name: "BoxPlotExample",
    async mounted() {
      const parsed = await d3.csvParse(data);
      console.log(parsed);

      const xScale = d3.scaleLinear().domain([1, 8]).range([20, 470]);
      const yScale = d3.scaleLinear().domain([0, 100]).range([480, 20]);

      const yAxis = d3.axisRight(yScale).ticks(8).tickSize(-470);

      d3.select(this.$refs.boxPlotTarget)
        .append("g")
        .attr("transform", "translate(470, 0)")
        .attr("id", "yAxisG")
        .call(yAxis);

      const xAxis = d3.axisBottom(xScale)
        .tickSize(-470)
        .tickValues([1,2,3,4,5,6,7])

      d3.select(this.$refs.boxPlotTarget)
        .append("g")
        .attr("transform", "translate(0, 480)")
        .attr("id", "xAxisG")
        .call(xAxis);

      d3.select(this.$refs.boxPlotTarget)
        .selectAll("circle.median")
        .data(parsed)
        .enter()
        .append("circle")
        .attr("class", "tweets")
        .attr("r", 5)
        .attr("cx", d => xScale(d.day))
        .attr("cy", d => yScale(d.median))
        .style("fill", "darkgray");

      d3.select(this.$refs.boxPlotTarget)
        .selectAll("g.box")
        .data(parsed).enter()
        .append("g")
        .attr("class", "box")
        .attr("transform", d => `translate(${xScale(d.day)},${yScale(d.median)})`)
        .each((d, i, els) => {
          d3.select(els[i])
            .append("rect")
            .attr("width", 20)
            .attr("x", -10)
            .attr("y",  yScale(d.q3) - yScale(d.median))
            .attr("height", yScale(d.q1) - yScale(d.q3))
            .style("fill", "white")
            .style("stroke", "black")
        })
    },
  }
</script>

<style scoped>

</style>

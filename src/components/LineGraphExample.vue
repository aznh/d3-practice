<template>
  <svg style="width: 800px; height: 800px;" ref="lineGraphTarget"></svg>
</template>

<script>
  import * as d3 from "d3";
  const data = `day,tweets,retweets,favorites
1,1,2,5
2,6,11,3
3,3,8,1
4,5,14,6
5,10,29,16
6,4,22,10
7,3,14,1
8,5,18,7
9,1,30,22
10,4,16,15`

  export default {
    name: "LineGraphExample",
    async mounted() {
      const parsed = await d3.csvParse(data);

      const xScale = d3.scaleLinear().domain([1, 10.5]).range([20, 480])
      const yScale = d3.scaleLinear().domain([0, 35]).range([480, 20])

      const xAxis = d3.axisBottom(xScale).tickSize(480).tickValues([1,2,3,4,5,6,7,8,9,10]);
      d3.select(this.$refs.lineGraphTarget).append("g").attr("id", "xAxisG").call(xAxis);

      const yAxis = d3.axisRight(yScale).ticks(10).tickSize(480);
      d3.select(this.$refs.lineGraphTarget).append("g").attr("id", "yAxisG").call(yAxis);

      d3.select(this.$refs.lineGraphTarget)
        .selectAll("circle.tweets")
        .data(parsed)
        .enter()
        .append("circle")
        .attr("class", "tweets")
        .attr("r", 5)
        .attr("cx", d => xScale(d.day))
        .attr("cy", d => yScale(d.tweets))
        .style("fill", "black");

      d3.select(this.$refs.lineGraphTarget)
        .selectAll("circle.retweets")
        .data(parsed)
        .enter()
        .append("circle")
        .attr("class", "retweets")
        .attr("r", 5)
        .attr("cx", d => xScale(d.day))
        .attr("cy", d => yScale(d.retweets))
        .style("fill", "lightgray");

      d3.select(this.$refs.lineGraphTarget)
        .selectAll("circle.favorites")
        .data(parsed)
        .enter()
        .append("circle")
        .attr("class", "favorites")
        .attr("r", 5)
        .attr("cx", d => xScale(d.day))
        .attr("cy", d => yScale(d.favorites))
        .style("fill", "gray");

      const tweetLine = d3.line().x(d => xScale(d.day)).y(d => yScale(d.tweets)).curve(d3.curveCardinal);

      d3.select(this.$refs.lineGraphTarget)
        .append("path")
        .attr("d", tweetLine(parsed))
        .attr("fill", "none")
        .attr("stroke", "darkred")
        .attr("stroke-width",  2)
    }
  }
</script>

<style scoped>

</style>

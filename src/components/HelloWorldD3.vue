<template>
  <div id="hello-world-d3"></div>
</template>

<script>
  import * as d3 from "d3"

  export default {
    name: "HelloWorldD3",
    mounted() {
      d3.select("#hello-world-d3")
        .append("div")
        .style("border", "1px black solid")
        .html("hello world")

      d3.select("#hello-world-d3 div")
        .style("background-color", "pink")
        .style("font-size", "24px")
        .attr("id", "newDiv")
        .attr("class", "d3div")
        .on("click", () => {
          console.log("You clicked a div")
        });
    }
  }
</script>

<style scoped>

</style>

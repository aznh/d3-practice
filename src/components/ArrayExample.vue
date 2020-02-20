<template>
  <div id="array-example"></div>
</template>

<script>
  import * as d3 from "d3";

  export default {
    name: "ArrayExample",
    data() {
      return {
        someNumbers: [17, 82, 9, 500, 40],
        someColors: ["blue", "red", "chartreuse", "orange"]
      }
    },
    mounted() {
      const smallerNumbers = this.someNumbers.filter(el => el <= 40)
      d3.select("#array-example")
        .data(smallerNumbers)
        .enter()
        .append("div")
        .html(d => {
          console.log(d)
          return d;
        });
    }
  }
</script>

<style scoped>

</style>

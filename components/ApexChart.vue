<template>
  <div id="chart">
    <client-only>
      <apexchart
        type="line"
        height="520"
        :options="data.chartOptions"
        :series="data.series"
      ></apexchart>
    </client-only>
  </div>
</template>

<script>
export default {
  props: ['data']
};
</script>
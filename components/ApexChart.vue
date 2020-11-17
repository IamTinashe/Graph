<template>
  <section>
    <div id="chart">
      <client-only>
        <apexchart
          type="line"
          height="500"
          :options="data.chartOptions"
          :series="data.series"
        ></apexchart>
      </client-only>
    </div>
  </section>
</template>

<script>
export default {
  props: ['data']
};
</script>
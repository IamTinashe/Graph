<template>
  <div class="small">
    <h1 class="title">
      Стоимость квадратного метра в квартире площадью 41-54, 99 м2
      <br><span>в евро vs. в унциях золоте</span>
    </h1>
    <ApexChart v-bind:data="{chartOptions, series}"/>
  </div>
</template>

<script>
import series from "@/assets/json/series.json"
import chartOptions from "@/assets/json/chartOptions.json"
export default {
  components: {
    'ApexChart': () => import('@/components/ApexChart')
  },
  data() {
    return {
      series: series.data,
      chartOptions: {
        chart: chartOptions.data.chart,
        stroke: chartOptions.data.stroke,
        plotOptions: chartOptions.data.plotOptions,
        colors: chartOptions.data.colors,
        labels: chartOptions.data.labels,
        markers: chartOptions.data.markers,
        xaxis: chartOptions.data.xaxis,
        yaxis: chartOptions.data.yaxis,
        tooltip: {
          shared: true,
          intersect: false,
          y: {
            formatter: function (y) {
              var value = y;
              if (typeof y !== "undefined") {
                if(y > 500) value =  '€ ' + y;
              }
              return value;
            },
          },
        },
      },
    };
  },
};
</script>

<style>
  .small .title{
    margin: auto;
    text-align: center;
    font-weight: 400;
    font-size: 22px;
    max-width: 60%;
    margin-top: 20px;
    line-height: 1;
  }
  .small .title span{
    font-size: 16px;
  }
</style>
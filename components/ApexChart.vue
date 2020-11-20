<template>
  <section class="container">
    <div class="row">
      <div class="col-6">
        <button @click="increaseLeft()" class="button left-position">+</button>
      </div>
      <div class="col-6">
        <button @click="increaseRight()" class="button right-position">+</button>
      </div>
    </div>
    <div id="chart">
      <client-only>
        <apexchart
          type="line"
          height="450"
          :options="data.chartOptions"
          :series="data.series"
          :key="index"
        ></apexchart>
      </client-only>
    </div>
    <div class="row">
      <div class="col-6">
        <button @click="decreaseLeft()" class="button left-position">-</button>
      </div>
      <div class="col-6">
        <button @click="decreaseRight()" class="button right-position">-</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ['data'],
  data(){
    return{
      index: 0,
      left: 3600,
      right: 6
    }
  },
  methods: {
    increaseLeft(){
      this.left = this.left + 500
      this.data.chartOptions.yaxis[0].max = this.left
      this.index++
    },
    increaseRight(){
      this.right = this.right + 2
      this.data.chartOptions.yaxis[1].max = this.right
      this.index++
    },
    decreaseLeft(){
      if(this.data.chartOptions.yaxis[0].max > 500){
        this.left = this.left - 500
        this.data.chartOptions.yaxis[0].max = this.left
        this.index++
      }
    },
    decreaseRight(){
      if(this.data.chartOptions.yaxis[1].max > 2){
        this.right = this.right - 2
        this.data.chartOptions.yaxis[1].max = this.right
        this.index++
      }
    }
  },
};
</script>

<style scoped>
.left-position{
  margin-left: 50px;
}

.right-position{
  float: right;
  margin-right: 110px;
}

.button {
	box-shadow:inset 0px 1px 0px 0px #d9fbbe;
	background:linear-gradient(to bottom, #b8e356 5%, #a5cc52 100%);
	background-color:#b8e356;
	border-radius:6px;
	border:1px solid #83c41a;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:15px;
	font-weight:bold;
	padding:0px 8px;
	text-decoration:none;
	text-shadow:0px 1px 0px #86ae47;
}
.button:hover {
	background:linear-gradient(to bottom, #a5cc52 5%, #b8e356 100%);
	background-color:#a5cc52;
}
.button:active {
	position:relative;
	top:1px;
}
</style>
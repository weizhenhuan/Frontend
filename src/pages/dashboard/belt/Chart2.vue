<template>
  <div ref="testLine" id="testLine" style="width:600px; height:300px"></div>
</template>


var ydata = [1,2,3]
<script>
export default {
  name: 'DisplayDraw',
  // ydata : [1,2,3,],
  data () {
    return {
      ydata : [0.5,0.6,0.2,0.3,0.7,0.2,0.6],
      myChart: null,
      option: {
        xAxis: {
          type: 'category',
          data: [0,5,10,15,20,25,30],
          name: '时间'
        },
        yAxis: {
          type: 'value',
          name: '油压/Mpa'
        },
        series: [{
          data: this.ydata,
          showSysbol:false,
          type: 'line'
        }],
      }
    }
  },
  methods: {
    addData : function() {
      this.ydata.shift();
      this.ydata.push(Math.random(1));
      this.option.series[0].data = this.ydata;
      this.myChart.setOption(this.option);
    }
  },
  mounted () {
    this.myChart = this.$echarts.init(this.$refs.testLine)
    this.myChart.setOption(this.option)
    setInterval(this.addData,1000)
  },
  
}
</script>

<style>
</style>
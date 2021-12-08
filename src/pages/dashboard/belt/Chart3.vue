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
      ydata : [1,3,5,2,4,1,2,3,4,5,1,2,3,3,2,1,2,2,5,4,4,3,2,1,1,1,2,2,3,],
      myChart: null,
      option: {
        xAxis: {
          type: 'category',
          data: [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30],
          name: '时间'
        },
        yAxis: {
          type: 'value',
          name: '速度m/s'
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
      this.ydata.push(Math.random(1) * 5);
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
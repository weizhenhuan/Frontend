<template>
  <div ref="testLine" id="testLine" style="width:600px; height:300px"></div>
</template>


var ydata = [1,2,3]
<script>
export default {
  name: 'DisplayDraw',
  data () {
    return {
      ydata : [110,120,130,110,45,34,12,82,16,40,130,142,106,108,51,19,45,18,65,142,143,129,110,142,52,16,27,121,106,45],
      myChart: null,
      option: {
        xAxis: {
          type: 'category',
          data: [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30],
          name: '时间'
        },
        yAxis: {
          type: 'value',
          name: '电流/A'
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
      this.ydata.push(Math.random(1) * 150);
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
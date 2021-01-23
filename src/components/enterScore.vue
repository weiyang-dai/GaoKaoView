<template>
    <div>
        <div class="buttonShow">
            <button class="mybutton">上一年</button>
            <p>{{year}}</p>
            <button class="mybutton">下一年</button>
        </div>
        <div class="enterScore" ref="enterScore"></div>
    </div>
</template>

<script>
import $ from 'jquery'
let echarts = require("echarts");

export default {
  name: 'enter',
  data () {
    return {
        year:'2020'
    }
  },
mounted(){
    this.drawLine();
  },
  methods: {
   drawLine(){
       console.log("执行")
    // 基于准备好的dom，初始化echarts实例
    var bar_dv = this.$refs.enterScore;
        if (bar_dv){
          console.log('bar_dv不为空');
          let myChart = this.$echarts.init(bar_dv)
    var option = {
    tooltip: {
        trigger: 'axis',
        axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
        }
    },
    legend: {
        data: ['本科一批', '本科二批']
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: {
        type: 'value'
    },
    yAxis: {
        type: 'category',
        data: ['四川', '江苏', '河南', '河北']
    },
    series: [
        {
            name: '本科一批',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight'
            },
            data: [320, 302,456,566]
        },
        {
            name: '本科二批',
            type: 'bar',
            stack: '总量',
            label: {
                show: true,
                position: 'insideRight'
            },
            data: [120, 132,345,656]
        }
    ]
};
      myChart.setOption(option);
}
}}}
</script>

<style scoped>
.enterScore{
  width: 400px;
  height: 500px;
  margin-top: 10%
}
.mybutton{
     width: 100px;
}
.buttonShow{
    position: absolute;
    height: 5%;
    display: flex;
    top: 0px;
}
</style>

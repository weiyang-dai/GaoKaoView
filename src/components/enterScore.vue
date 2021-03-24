<template>
    <div>
        <div class="buttonShow">
            <!-- <button class="mybutton">上一年</button> -->
            <p>{{location}}历年录取线</p>
            <!-- <button class="mybutton">下一年</button> -->
        </div>
        <div class="enterScore" ref="enterScore"></div>
    </div>
</template>

<script>
import $ from 'jquery'
import Score from '../../static/enterScore.json'
let echarts = require("echarts");

export default {
  name: 'enter',
  data () {
    return {
        location:'四川'
    }
  },
mounted(){
    this.drawLine();
  },
  methods: {
   drawLine(){
    var years=Score[0]['years']
    var province=Score[0]['province']
    var lable=Score[0]['lable']
    this.location=province
    var data=[]
    for(let i in years)
    {
        let obj= {
            name: years[i],
            type: 'bar',
            //stack: '总量',
            label: {
                show: true,
                position: 'insideRight'
            },
            data:Score[0][ years[i]]
        }
        data.push(obj)
    }
    // 基于准备好的dom，初始化echarts实例
    var bar_dv = this.$refs.enterScore;
        if (bar_dv){
          let myChart = this.$echarts.init(bar_dv)
    var option = {
    tooltip: {
        trigger: 'axis',
        axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
        }
    },
    legend: {
        data:years
    },
    grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
    },
    xAxis: {
        type: 'value',
        nameTextStyle:{
            fontWeight: "bolder",
            color: "rgba(0, 0, 0, 1)",
            fontSize :12
        },
       axisLine: {
                lineStyle: {
                    color: "#fff",
                }
            }

    },
    yAxis: {
        type: 'category',
        data:lable,
         axisLine: {
                lineStyle: {
                    color: "#fff",
                }
            }
    },
    series:data
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

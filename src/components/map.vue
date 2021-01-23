<template>
  <div class="mapContainer" ref="chart">
  </div>
</template>

<script>
import $ from 'jquery'
import china from '../../static/china.json'
let echarts = require("echarts");

export default {
  name: 'mymap',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
    }
  },
mounted(){
    this.drawLine();
  },
  methods: {
   drawLine(){
    console.log(china)
    // 基于准备好的dom，初始化echarts实例

    var mydata =  [{
      name:"合肥",
      value:[117.27,31.86]
    },
    {
      name:"武汉",
      value:[114.31,30.52]
    },
    {
      name:"长沙",
      value:[113,28.21]
    }]
    var bar_dv = this.$refs.chart;
        if (bar_dv){
          console.log('bar_dv不为空');
          let myChart = this.$echarts.init(bar_dv)
          echarts.registerMap("china", china);

      var option = {
        baseOption: {
          backgroundColor: " #004A80",
          title: {
            text: "全国大学地图",
            x: "center"
          },
          tooltip: {
            show: false
          },
          geo: {
            map: "china",
            center: [108.9199, 33.1904],
            zoom: 0,
            itemStyle: {
              shadowBlur: 5
            },
            roam: true,
            scaleLimit: {
              min: 1,
              max: 10
            }
          },
          //触碰文字
          tooltip: {
            trigger: "item",
          },
          series: [
            {
              type: "effectScatter",
              coordinateSystem: "geo",
              data: mydata,
              symbolSize: 12,
              label: {
                normal: {
                  show: false
                },
                emphasis: {
                  show: false
                }
              },
              itemStyle: {
                emphasis: {
                  borderColor: "#fff",
                  borderWidth: 1
                }
              }
            }
          ]
        }
      };
      myChart.setOption(option);
}
}}}
</script>

<style scoped>
.mapContainer{
  width: 1000px;
  height: 600px;
}
</style>

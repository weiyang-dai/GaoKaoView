<template>
     <div id="highCharts" class="chartsConter"></div>
</template>

<script>
import Highcharts from "highcharts/highcharts";
import wordcloud from "highcharts/modules/wordcloud";
import $ from 'jquery'
wordcloud(Highcharts);
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
     chartsData: [
        {
          name: "北京大学",
          weight: 30,
        },
        {
          name: "清华大学",
          weight: 22,
        },
        {
          name: "浙江大学",
          weight: 35,
        },
        {
          name: "江苏大学",
          weight: 40,
        },
        {
          name: "南京大学",
          weight: 20,
        }]
    }
  },
   mounted(){
         this.initClassHighCharts(this.chartsData);
      },
  methods: {
  // 初始化HighCharts
  initClassHighCharts(data) {
    Highcharts.chart("highCharts", {
      // 关闭Highcharts右下方logo
      credits: { enabled: false },
      chart:{
          backgroundColor: '#145b7d',
      },
      series: [
        {
        // 把字摆正
          rotation: {
            from: 0,
            to: 0,
            orientations: 5,
          },
          type: "wordcloud",
          data: data,
        },
      ],
      title: {
        text: "词云",
      },
    });
  },}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#highCharts{
    width: 200px;
    height: 200px;
}
</style>

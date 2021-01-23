<template>
   <div class="app">
           <!-- <div class="head">head</div> -->
           <div class="container">
                <div class="left-group">left-group</div>
                <div class="mid-group">
                  <mymap></mymap>
                </div>
                <div class="right-group">
                    <enterScore></enterScore>
                </div>
           </div>
           <div class="foot">foot</div>
      </div>

</template>

<script>
import mymap from './components/map';
import enterScore from './components/enterScore';
export default {
  name: 'App',
  components:{
    mymap,
    enterScore
    },
    data: function () {
      return {
      }
    }
}
</script>

  <style>
        /* 三栏布局，中间自适应高度... */
        * {
            margin: 0;
            padding: 0;
        }    
        /* .head{
            height: 100px;
            width: 100%;
            background-color: gold;
            text-align: center;
        } */
        .container{
            position: absolute;
            width: 100%;
            display: flex;
            top: 0px;
            bottom: 100px;
        }
        .left-group, .right-group{
            width: 400px;
            background-color: #7ecff2;
            text-align: center;
        }
        .mid-group{
            flex: 1;
            text-align: center;
        }
        .foot{
            position: absolute;
            width: 100%;
            height: 250px;
            bottom: 0;
            background-color: purple;
            text-align: center;
        }

</style>

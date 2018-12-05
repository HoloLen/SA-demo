<template>
  <div id="app">
    <h2>海事视频专网安全态势感知系统</h2>
    <br>
    <TreeChart :json="data" :class="{landscape: landscape.length}" @click-node="clickNode" />
    <Note :json="data"></Note>
  </div>
</template>

<script>
  import TreeChart from "@/components/TreeChart";
  import data0 from "../static/data/0.json";
  import data1 from "../static/data/1.json";
  import data2 from "../static/data/2.json";
  import data3 from "../static/data/3.json";
  import data4 from "../static/data/4.json";
  import data5 from "../static/data/5.json";
  import data6 from "../static/data/6.json";
  import data7 from "../static/data/7.json";
  import data8 from "../static/data/8.json";
  import data9 from "../static/data/9.json";
  import data10 from "../static/data/10.json";
  import data11 from "../static/data/11.json";
  import data12 from "../static/data/12.json";
  import data13 from "../static/data/13.json";
  import data14 from "../static/data/14.json";
  import data15 from "../static/data/15.json";
  import data16 from "../static/data/16.json";
  import data17 from "../static/data/17.json";
  import data18 from "../static/data/18.json";
  import data19 from "../static/data/19.json";
  import data20 from "../static/data/20.json";
  import data21 from "../static/data/21.json";
  import data22 from "../static/data/22.json";
  import data23 from "../static/data/23.json";
  import data24 from "../static/data/24.json";

  import Note from "@/components/Note";

  export default {
    name: 'app',
    components: {
      TreeChart,
      Note
    },
    data() {
      return {
        landscape: [],
        data: data0
      }
    },
    methods: {
      clickNode: function(node){
        // eslint-disable-next-line
        console.log(node)
      },
      random(lower, upper) {
        return Math.floor(Math.random() * (upper - lower+1)) + lower;
      }
    },
    mounted() {
      let datas = [data1, data2, data3,data4, data5, data6, data7,data8, data9, data10, data11,data12, data13, data14, data15,data16,data17,data18,data19,data20,data21,data22,data23,data24]
      let times = [0]
      setTimeout(()=> {
        for (let i = 0; i < 25; i++) {
          times.push(this.random(3000, 7000)+times[i])
        }
        for (let j = 0; j < 25; j++) {
          setTimeout(()=>{
            this.data = datas[j]
          },times[j+1])
        }
      }, 500)

    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ddd;
    margin-top: 20px;
  }
  #app .avat{border-width:0px;}
  #app .name{font-weight:500; font-size: 12px;}
</style>

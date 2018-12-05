<template>
  <div id="box">
    <ul id="con1" ref="con1" :class="{anim:animate==true}">
      <li v-for='item in items'>{{item.ip}}--{{item.type}}--{{item.madeIn}}--{{item.port}}--{{item.problem}}</li>
    </ul>
  </div>
</template>
<script>
  export default {
    props: ["json"],
    data() {
      return {
        animate: false,
        temp: [
          {ip:'198.17.80.242', type:'路由器', madeIn:'D-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.89.2', type:'路由器', madeIn:'TP-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.97.244', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.89.123', type:'路由器', madeIn:'TP-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.89.102', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.65.5', type:'路由器', madeIn:'TP-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.97.200', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.97.112', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.97.244', type:'DVR', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.65.123', type:'路由器', madeIn:'D-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.89.125', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.65.233', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.138.211', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.138.210', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.65.133', type:'路由器', madeIn:'D-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.143.80', type:'路由器', madeIn:'TP-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.66.203', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.143.81', type:'路由器', madeIn:'D-link', port:23, problem:'telnet弱口令'},
          {ip:'198.17.64.157', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.66.202', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.66.125', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.66.130', type:'摄像头', madeIn:'海康', port:8000, problem:'客户端弱口令'},
          {ip:'198.17.66.126', type:'DVR', madeIn:'海康', port:8000, problem:'客户端弱口令'},
        ],
        items:[],
        i: 0
      }
    },
    created() {
      setInterval(this.scroll, 2000)
    },
    watch: {
      json: {
        handler: function () {
          this.items = this.temp.slice(0,this.i++)
        },
        immediate: true
      }
    },
    methods: {
      scroll() {
        this.animate = true;    // 因为在消息向上滚动的时候需要添加css3过渡动画，所以这里需要设置true
        setTimeout(() => {      //  这里直接使用了es6的箭头函数，省去了处理this指向偏移问题，代码也比之前简化了很多
          this.items.push(this.items[0]);  // 将数组的第一个元素添加到数组的
          this.items.shift();               //删除数组的第一个元素
          this.animate = false;  // margin-top 为0 的时候取消过渡动画，实现无缝滚动
        }, 800)
      }
    }
  }
</script>

<style>
  *{
    margin: 0 ;
    padding: 0;
  }
  #box{
    z-index: 9999;
    position: fixed ! important;
    right: 0px;
    top:80px;
    width: 280px;
    height: 550px;
    overflow: hidden;
    padding-left: 10px;
    border: 2px solid white;
  }
  .anim{
    transition: all 0.5s;
    margin-top: -30px;
  }
  #con1 li{
    list-style: none;
    line-height: 30px;
    height: 30px;
    font-size: 12px;
    color: yellow;
  }
</style>

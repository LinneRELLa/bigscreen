<template>
  <div id="app">
   
    <div id="content">
  
       
    <div id="header">
      <div id="title">可视化展板</div>
      <div id="time">当前时间:{{timeext}}</div>

    </div>
    <div id="section">
      <div id="container"></div>
        <div id="middle">
          <div id="main"> 
            
          </div>

        </div>
    <div id="left">
      <div id="square"></div>
      <div id="line"></div>
      <div id="sector"> </div>




    </div>
  
    <div id="right">
      
   <div id="squareR" class="echarts"></div>
      <div id="lineR" class="echarts"></div>
      <div id="sectorR" class="echarts"> </div>

    </div>
    </div>
        
   </div>
  
  </div>
</template>

<script>


export default {
  name: 'App',
  computed:{
       timeext(){
        const d=this.time
        return d.getFullYear()+'年'+d.getMonth()+'月'+d.getDate()+'日'+
        d.getHours().toString().padStart(2,'0')+':'+d.getMinutes().toString().padStart(2,'0')+':'+d.getSeconds().toString().padStart(2,'0');
       }
  },
  data(){
    return {
      time:new Date(),
    }
  },
  components: {

  },
  created(){
    const vm=this;
    setInterval(()=>{vm.time=new Date()},1000);

  },
  mounted(){
    (function square(){

var chartDom = document.getElementById('square');
var myChart = echarts.init(chartDom);
var option;

option = {

  title:{
text:'柱状图-就业行业',
textStyle:{
  color:'white'
},

  },
  grid:{


containLabel: true,
left:'10',
},

  xAxis: {
    axisLabel:{
      interval: 0,

textStyle:{
  color:'white',
}
    },
    nameTextStyle:{
      color:'white'
    },
    type: 'category',
    data: ['旅游', '教培', '游戏', '医疗', '电商', '社交', '金融']
  },
  yAxis: {

    type: 'value',
         axisLabel:{

textStyle:{
  color:'white',
}},

  },
  series: [
    {
      data: [120, 200, 150, 80, 70, 110, 130],
      type: 'bar',
      itemStyle:{
        color:'rgb(69,128,208)',
        barBorderRadius:8
      }
    }
  ]
};

option && myChart.setOption(option);

    })();

          
(function line(){
var chartDom = document.getElementById('line');
var myChart = echarts.init(chartDom);
var option;

option = {

        color: ['red','blue'],
  title: {
    text: '折线图-人员特点',
    left:'center',
    textStyle:{
  color:'white'
}
  },
  tooltip: {
    trigger: 'axis'
  },
  legend: {
    top:'8%',
    data: ['新增粉丝','新增游客'],
        textStyle:{
  color:'white',
}
  },
  grid: {
    left: '3%',
    right: '4%',
    bottom: '3%',
    containLabel: true
  },

  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
     axisLabel:{
        textStyle:{
  color:'white',
}
}
  },
  yAxis: {
    type: 'value',
    axisLabel:{
        textStyle:{
  color:'white',
}
}
 
  },
  series: [
    {
      name: '新增粉丝',
      type: 'line',
      stack: 'Total',
      data: [120, 132, 101, 134, 90, 230, 210],
      smooth:true,
    },
    {
      name: '新增游客',
      type: 'line',
      stack: 'Total',
      data: [220, 182, 191, 234, 290, 330, 310],
      smooth:true,
    }
   
  ]
};

option && myChart.setOption(option);


})();

(function sector(){


var chartDom = document.getElementById('sector');
var myChart = echarts.init(chartDom);
var option;

option = {
     grid: {
              left: '1%',
              right: '1%',
              bottom: '6%',
              containLabel: true
          },
  tooltip: {
    trigger: 'item'
  },
  title:{
    text:'饼形图-年龄分布',
    left:'center',
    textStyle:{
      color:'white',
    }
  },

  series: [
    {
      
      name: 'Access From',
      type: 'pie',
      radius: ['30%', '60%'],

      avoidLabelOverlap: false,
      top:0,
      itemStyle: {
        borderRadius: 10,
        borderColor: '#fff',
        borderWidth: 2
      },
      label: {
        show: false,
        position: 'center'
      },
      emphasis: {
        label: {
          show: true,
          fontSize: '40',
          fontWeight: 'bold'
        }
      },
      labelLine: {
        show: false
      },
      data: [
        { value: 1048, name: '直接访问' },
        { value: 735, name: '邮件营销' },
        { value: 580, name: '联盟广告' },
        { value: 484, name: '视频广告' },
        { value: 300, name: '搜索引擎' }
      ]
    }
  ]
};

option && myChart.setOption(option);


})();
(function lineR(){

var chartDom = document.getElementById('lineR');
var myChart = echarts.init(chartDom);
var option;

option = {
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
    axisLabel:{
        textStyle:{
      color:'white'
    }
    }
  },
  yAxis: {
    type: 'value',
    axisLabel:{
        textStyle:{
      color:'white'
    }
    }
  },
  title:{
    text:'折线图-播放量',
    textStyle:{
      color:'white'
    },
    left:'center'

  },
  legend: {
    top:25,
    data: ['播放量', '转发量'],
    textStyle:{
      color:'white'
    }
  },
  series: [
    {
      name: '播放量',
      data: [820, 632, 901, 634, 1290, 1230, 1020],
      type: 'line',
      areaStyle: {},
      smooth: true
    },
    {
      name: '转发量',
      data: [35, 999, 101, 934, 82, 1330, 73],
      type: 'line',
      areaStyle: {},
      smooth: true
    }
  ]
};

option && myChart.setOption(option);


})();
(function squareR(){
  var chartDom = document.getElementById('squareR');
var myChart = echarts.init(chartDom);
var option;
var mc=['pink','blue','red','black'];
option = {

  title: {
    text: '柱状图-技能掌握',
    left:'center',
    textStyle:{
      color:'white'
    }
  },
  tooltip: {
    trigger: 'axis',
    axisPointer: {
      type: 'shadow'
    }
  },
 
  grid: {
    top:"10%",
    left: '22%',
    bottom: '10%',
    containLabel: false
  },
  xAxis: {
    show:false,
  },
  yAxis: [{
    
    axisLabel:{
textStyle:{
  color:'white',
}},
    axisLine:{
      show:false
    },
  axisTick:{
      show:false
    },
 
    type: 'category',
    data: ['H5','CSS','JS','VUE','NODE'],
  },
 {
    right:0,
    axisLabel:{
textStyle:{
  color:'white',
}},
    axisLine:{
      show:false
    },
  axisTick:{
      show:false
    },
 
    type: 'category',
    data: [70,34,60,78,69],
  }],
  series: [
    {yAxisIndex:0,
      name: 'content',
    type: 'bar',
  barCategeoryGap:50,
  barWidth:10,
     label:{
        normal:{
          show:true,
          position:'inside',
          formatter:"{c}%"
        }
      },
  itemStyle:{
  
     
barBorderRadius:20,
     color:
  function(params){
    console.log('1')
    console.log(params);
    const n=mc.length
    return mc[params.dataIndex%n]
   },
 


  },


      data:  [70,34,60,78,69],
    },
    {yAxisIndex:1,
      name: 'outer',
    type: 'bar',
  barCategeoryGap:50,
  barWidth:15,

  itemStyle:{
  
     
barBorderRadius:20,
     color:'none',
     borderColor:'white',
     borderWidth:3,
     barBorderRadius:15
 


  },


      data: [100,100,100,100,100]
    },



  ]
};

option && myChart.setOption(option);

})();

(function sectorR()

{

var chartDom = document.getElementById('sectorR');
var myChart = echarts.init(chartDom);
var option;

option = {
  title: {
    text: '饼形图-地区分布',
    left:'center',
   textStyle:{
    color:'white',
   }
    
  },
       grid: {
              left: '1%',
              right: '1%',
              bottom: '6%',
              containLabel: true
          },
  tooltip: {
    trigger: 'item',
    formatter: '{a} <br/>{b} : {c} ({d}%)'
  },
  legend: {
    left: 'center',
    top: 'bottom',
    data: [
      'rose1',
      'rose2',
      'rose3',
      'rose4',
      'rose5',
      'rose6',
      'rose7',
      'rose8'
    ]
  },

  series: [
    { 

      name: 'Area Mode',
      type: 'pie',
      radius: [20, 70],
      center: ['50%', '50%'],
      roseType: 'radius',
      itemStyle: {
        borderRadius: 5
      },
 
      data: [
        { value: 20, name: '北京' },
        { value: 23, name: '上海' },
        { value: 28, name: '广东' },
        { value: 22, name: '深圳' },
        { value: 20, name: '云南' },
        { value: 15, name: '南昌' },
        { value: 12, name: '山东' },
        { value: 10, name: '九江' }
      ]
    }
  ]
};

option && myChart.setOption(option);
})()


   const map = new AMap.Map('container',{
    zoom:5,
    center:[ 109.28911404445773,43.174367]
      
 
   });
 map.setFitView()
    window.map=map;

       const styleName = 'amap://styles/0ba598ed53d8cd5e34a6416881cbf555';//底部颜色
            map.setMapStyle(styleName);
            console.log(map.resize)
  }
}



</script>

<style lang="less">
.middle{
   position:absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%,-50%);
}
.opa{
    background:linear-gradient(rgba(255,255,255,0.1),rgba(255,255,255,0),rgba(255,255,255,0.1));
}
*{

  margin: 0;
  box-sizing: border-box;
}
html,body{

   width: 100%;

     overflow: hidden;

}

#app {
  
  width: 10rem;
 
  display: flex;
  flex-direction: column;
   
  #header{

    z-index:3;
  .opa();
    width: 100%;
    height: 100px;
    position: absolute;
    top: 0;
 
    color:white;
    #title{
      font-size:35px;
    
     .middle()
    }
    #time{ position:absolute;
      right: 0;
      top: 50%;
      font-size: 20px;
      transform: translateY(-50%);

    }
  }
  #section{
    min-width: 800px;
    z-index: 2;
      width: 100%;
    height: calc(100% - 100px);
    position: absolute;
    top: 100px;

  }
  #content{
    flex: 1;
    overflow: hidden;
    #left{
  
      #square{
        width: 400px;
        padding: 0 20px;
        height:300px;
        border:0.5px solid white;
      }
      #line{
         width: 400px;
    border:0.5px solid white;
        height:300px;
}
      #sector{
          width: 400px;
    border:0.5px solid white;
        height:300px;
}
       .opa();
      
      
      
         position:absolute;
       left: 0;
      width: 400px;
      height: 100%;
           z-index:1;


    }
    #right{ z-index:4;
       .opa();
       position:absolute;
       right: 0;
      width: 400px;
      height: 100%;
      margin-left:-400px;
  

          
    }
    #middle{

   
           z-index: -1;
   position:absolute;
   left: 400px;
   right: 400px;
        height: 100%;
  
        margin: 0 400px;
    }
  }

}

  #container{
    position:absolute;
    top: -400px;
    width: 100%;
   height: calc(100% + 400px);

  }
.echarts{
  width: 400px;
  height: 300px;
  border:1px solid black;
}
</style>

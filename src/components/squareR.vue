<template>
	

	<div ref="squareR" class="echarts"></div>
</template>


<script>
	
export default{

	name:'squareR',
	mounted(){
		(function squareR(){
  var chartDom = this.$refs.squareR
var myChart = echarts.init(chartDom);  
window.addEventListener('resize',()=>{
    myChart.resize()
  })
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

}).bind(this)();
	}
    

}

</script>
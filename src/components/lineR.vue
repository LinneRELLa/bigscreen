<template>
	

	<div ref="lineR" class="echarts"></div>
</template>


<script>
	
export default{

	name:'lineR',
	mounted(){
	(function lineR(){

var chartDom = this.$refs.lineR
var myChart = echarts.init(chartDom);
var option;
  window.addEventListener('resize',()=>{
     myChart.resize()
  })
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


}).bind(this)();
	}
    

}

</script>
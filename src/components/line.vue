<template>
	

	<div ref="lineC" class="echarts"></div>

</template>


<script>
	
export default{

	name:'lineC',
	mounted(){
		(function line(){
var chartDom = this.$refs.lineC
var myChart = echarts.init(chartDom);
var option;
  window.addEventListener('resize',()=>{
    myChart.resize()
  })
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


}).bind(this)();
	}
    

}

</script>
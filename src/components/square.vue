<template>
	
<div>
	<div ref="square" class="echarts"></div>
  </div>
</template>


<script>
	
export default{

	name:'square',
	mounted(){
		(function square(){

var chartDom = this.$refs.square
var myChart = echarts.init(chartDom);
var option;
  window.addEventListener('resize',()=>{
    myChart.resize()
  })
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

    }).bind(this)();
	}
    

}

</script>

<style scoped lang="less">
  

</style>
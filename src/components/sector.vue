<template>
	

	<div ref="sector" class="echarts"></div>
</template>


<script>
	
export default{

	name:'SECTOR',
	mounted(){
		(function sector(){


var chartDom = this.$refs.sector
var myChart = echarts.init(chartDom);
var option;
  window.addEventListener('resize',()=>{
    myChart.resize()
  })
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


}).bind(this)();
	}
    

}

</script>
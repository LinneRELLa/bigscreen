<template>
  

  <div ref="sectorR" class="echarts"></div>
</template>


<script>
  
export default{

  name:'sectorR',
  mounted(){
   (function sectorR()

{

var chartDom = this.$refs.sectorR
var myChart = echarts.init(chartDom);

  window.addEventListener('resize',()=>{
  console.log('1')
    myChart.resize()
  })
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
}).bind(this)()

  }
    

}

</script>
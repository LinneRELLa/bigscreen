<template>
  <div id="app">
   
    <div id="content">
  
       
    <div id="header">
      <div id="title">可视化展板</div>
      <div id="time">当前时间:{{timeext}}</div>

    </div>

    <div id="section">
     
     <div id="container"></div>
    <div id="left">
     <square/>
      <lineC/>
     <sector/>




    </div>
        <div id="middle">
          <div id="main" > 
            
          </div>

        </div>
  
    <div id="right">
      
    <squareR/>
      <lineR/>
     <sectorR/>

    </div>
    </div>
        
   </div>
  
  </div>
</template>

<script>
import square from './components/square'
import squareR from './components/squareR'
import lineC from './components/line'
import lineR from './components/lineR'
import sector from './components/sector'
import sectorR from './components/sectorR'

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
    square,
    squareR,
 lineC,
lineR,
sector,
 sectorR,

  },
  created(){
    const vm=this;
    setInterval(()=>{vm.time=new Date()},1000);

  },
  mounted(){

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
<style>
  html,body{
margin: 0 ;
   width: 1920px;
height: 1080px;
     

}

</style>
<style lang="less" scoped>


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

  margin: 0 !important;
  box-sizing: border-box;
}

#app {

  
  width: 100%;
  overflow: hidden; 
 height: 100%;
  display: flex;
  flex-direction: column;
   
  #header{

    z-index:3;
  .opa();
    width: 100%;
    height: 100px;
    position: relative;
    
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
    min-width: 1680px;
    z-index: 2;
    display: flex;
      width: 100%;
    
    position: relative;
   height: calc(100% - 100px)

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
      
      
      
       position:relative;
     flex: 2;
      height: 100%;
           z-index:1;
     display: flex;
     flex-direction:column;
     justify-content: space-between;

    }
    #right{ z-index:4;
         display: flex;
     flex-direction:column;
     justify-content: space-between;
       .opa();
     
         flex: 2;
      height: 100%;
      margin-left:-400px;
  

          
    }
    #middle{

   flex:5;
           z-index: -1;

        height: 100%;
  
        margin: 0 10px;
    }
  }

}

  #container{
    position:absolute;
    top: -40rem;
    width: 100%;
   height: calc(100% + 400px);

  }
::v-deep .echarts{
  width: 100%;
  height: 30rem;
  border:1px solid black;
}
</style>

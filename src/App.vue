<script setup>
import { computed, onMounted, ref } from 'vue';
  const progress = ref(0)

  // 針對捲軸監聽和區段計算座標、百分比
  onMounted(()=>{
    // 針對app取得scroll事件
    const app =document.querySelector('#app')
    app.addEventListener('scroll',function(){
     if(app.scrollTop < window.innerHeight){
       progress.value = 3

     } else if(app.scrollTop > window.innerHeight * 2){
       progress.value = 1
     }else{
       progress.value = 3 - 2 * ((app.scrollTop - window.innerHeight) /window.innerHeight)

     }
    })
  })
  const fixClass = computed(()=>{
    return progress.value > 1
  }) 

</script>

<template>
  <div class="section text">
    還是有下一步
  </div>
  <div id="section2" class="section" :style="{'--scale':progress}" :class="{sticky:fixClass}">
   
  </div>
  <div class="section text">該儲值咖啡信仰了
  </div>


</template>

<style>
*{
  margin: 0;
  padding: 0;
  }
  body{
    overflow: hidden;
  }
  #app{
    width: 100vw;
    height: 100vh;
    overflow: auto;
  }
  .section{
    position: relative;
    width: 100%;
    height: 100%;
    background-color: #fff;
    overflow: hidden;
  }
  .text{
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 100px;
  }
  #section2,#section3{
    background-color: black;
  } 

 

    #section2{
     --scale:3;
    } 

    #section3{     
       --scale:1;
    } 
  .sticky{
    position: sticky !important;
    top: 0;
    left: 0;
  }
  .static{
    position: static !important;

  }



  .phone{
    position: absolute;
    width: 100%;
    height: 100%;
    transform: scale(var(--scale));
  }
  .phone > *  {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);

  }
  .phone > img{
    clip-path: inset(15% 8% round 4%);
    width: 60%;
    height: auto;

  }
  .phone > .rect{
    width: 50%;
    height: 0;
    padding-top: 25%;
    border: 6px solid white;
    border-radius: 10px;
  }
 
</style>

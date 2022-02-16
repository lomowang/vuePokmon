<script setup>
 
</script>

<template>
  <div class="section text">
    怎樣把這麼大規模升級的相機塞進來？
  </div>
  <div id="section2" class="section">
    <div class="phone">
      <img src="https://picsum.photos/id/684/1920/1200">
      <div class="rect"></div>
    </div>

  </div>
  <div id="section3" class="section">
    <div class="phone">
      <img src="https://picsum.photos/id/684/1920/1200">
      <div class="rect"></div>
    </div>

  </div>
  <div class="section text">怎樣把這麼大規模升級的相機塞進來？</div>

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
      --scale:3
    } 
  #section3{
      --scale:1
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
    clip-path: inset(15% 8% round 5%);
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

<template>
  <root>
    <!--모달창-->
    <div class="black-bg" v-if="isModalOpen == true">
      <div class="white-bg">
        <h4>{{ onerooms[clickNo].title }}</h4>
        <p>{{ onerooms[clickNo].content }}</p>
        <p @click="isModalOpen = false">닫기</p>
      </div>
    </div>

    <div class ="menu">
      <a v-for="v in menulist" :key="v">{{ v }}</a>
    </div>

    <div v-for="(o,i) in onerooms" :key="o">
      <img :src="o.image" class="room-img">
      <h4 @click="isModalOpen = true;clickNo = i">{{ o.title }}</h4>
      
      <p>{{ o.price }}만원</p>
    </div>

  </root>
</template>

<script>
import oneroom from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return{
      clickNo  : '',
      onerooms : oneroom,
      isModalOpen : false,
      declar  : [0,0,0],
      menulist : ['Home','Products','About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸']
    }
  },
  methods : {
    increase(){
      this.declar[0] ++;
    }
  },
  components: {

  }
} 
</script>

<style>
body
{
  margin:0;
}
div
{
  box-sizing:border-box;
}
.black-bg
{
  width:100%;
  height:100%;
  background: rgba(0,0,0,0.5);
  position:fixed;
  padding:20px;
}
.white-bg
{
  width:100%;
  background:white;
  border-radius:8px;
  padding:20px;
}
.room-img
{
  width : 100%;
  margin-top:20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color:white;
  padding:10px;
}
</style>

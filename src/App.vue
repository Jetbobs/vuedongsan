// html 작성
<template>
<div >
    <div class="menu">
    <a v-for="a in menu" :key="a">{{ a }}</a>
  </div>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <div class="close_btn">
        <span @click="모달창열렸니 = false">닫기</span>
      </div>
    </div>
  </div>
  <div v-for="(a,i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <h4>{{원룸들[i].title}}</h4>
    <p> {{원룸들[i].price}}만원</p>
  </div>
  <div class="transition_test">
    <button @click="toggleModal">
      Open
    </button>
    <transition name="fade">
    <div v-if="isOpen" class="modal">
      <p>
        <button @click="toggleModal">Close</button>
      </p>
    </div>
    </transition>
  </div>
</div>
</template>
// js 작성
<script>

// eslint-disable-next-line 
import data from './assets/oneroom'

export default {
  name: 'App',
  data() {
    return {
      원룸들 : data,
      menu: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      price: [50, 60, 70],
      신고수: [0, 0, 0],
      모달창열렸니 : false,
      isOpen:false,
    }
  },
  methods: {
    increase() {
      this.신고수 += 1;
    },
    toggleModal(){
      this.isOpen=!this.isOpen
    }
  },
  components: {
  }
}
</script>
// css 작성
<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
<style lang="scss">
.black-bg {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;

  .white-bg {
    width: 100%;
    background-color: white;
    border-radius: 8px;
    padding: 20px;
  }
  .close_btn{
    span{
      cursor: pointer;
      background-color: #d7d7d7;
      padding: 5px;
    }
  }
}
.v-enter{
  opacity: 0;
}
.v-enter-active{
  transition: opcity 2s ease-in;
}
.v-leave-active{
  transition: opacity 2s ease-out;
}
.v-leave-to{
  opacity: 0;
}
</style>
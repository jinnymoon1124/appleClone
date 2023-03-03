<template>

  <Transition name="fade" >
    <Modal :data = "data"
    :detail = "detail"
    :click = "click"
    @closeModal="detail = false"
    /> 
  </Transition>  

    

  <div class="menu"> <!--상단바, 네비게이션-->
    <a v-for = "i in 메뉴들" :key="i">{{i}}</a>
  </div> 

  <Discount/>


  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>


  <Card @openModal="detail = true; click = $event"
  :data = "data[index]" v-for="(i, index) in data" :key="i"
  :vote = "vote[index]"
  @voteNum="vote[index]++"
  /> 


</template>


<script>

import data from './assets/data.js';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  data() {
    return {
      click : 0,
      vote : [0,0,0,0,0,0],
      data : data,
      dataOriginal : [...data],
      detail : false, // 0, false = 닫혔다 1, true = 열렸다
      메뉴들 : ['Home', 'Shop', 'About'],
    }
  },

  methods : {
    priceSort () {
      this.data.sort(function(a,b){
        return a.price - b.price
      })
    },
    sortBack() {
      this.data = [...this.dataOriginal];
    }
  },
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
  body {
    margin: 0
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

  .fade-enter-from {
    opacity: 0;
  }

  .fade-enter-active {
    Transition: all 1s;
  }

  .fade-enter-to {
    opacity: 1;
  }


  .fade-leave-form {
    opacity: 1;
  }

  .fade-leave-active {
    Transition: all 1s;
  }

  .fade-leave-to {
    opacity: 0;
  }

</style>





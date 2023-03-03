<template>
  <div class="black-bg" v-if="detail == true"> <!--모달창 : 조건식이 참일 경우에 작동-->
    <div class="white-bg">
      <h4>{{ data[click].title }}</h4>
      <p class="worldtime">{{ data[click].time }}</p>
      <img :src="data[click].detailimg" class="detailimage">
      <p>{{ data[click].content }}</p>
      <p>항공권 가격 : {{ data[click].price }}원</p>

      <input v-model.number="month"> 

      <p>수량 : {{ month }}   /  가격 : {{ data[click].price * month }}원</p>

      <div>
        <button @click="$emit('closeModal')">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name : "Modal",
  data() {
    return {
      month : 1,

    }
  },

  watch : {
    month (a) {
      if (a != Number) {
        alert('숫자를 입력해주세요'),
        a = 1 // 아직 수정 필요한부분
      }
    }
  },

  props : {
    data : Array,
    detail : Boolean,
    click : Number
  }
}
</script>

<style>
  .black-bg {
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    position: fixed;
    padding: 20px;
  }

  .white-bg {
    width: 100%;
    background: white;
    border-radius: 8px;
    padding: 20px;
  }

  .detailimage {
    width: 450px;
  }

  .worldtime {
    text-align: right;
    padding-right: 150px;
  }
</style>
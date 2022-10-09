<template>
  <div>
    <div>
    <div>
        <input type="text" v-model="numberOil">请输入炸油测试读数
     <div class="wrapper">
       <div v-if="numberOil>15" >
        <span>您的测试大于15，请用3M试纸测试是否可以使用</span>
        <div><input type="radio" value="green" v-model="color" >绿色 <input type="radio" value="yellow" v-model="color">黄色</div>
      </div>
     </div>
      <div>
        <button>提交测试结果</button>
      </div>
    </div>
      <h2>swiper轮播图</h2>
      <div class="swiper-container">
        <div class="swiper-wrapper">
          <div class="swiper-slide">Slide 1</div>
          <div class="swiper-slide">Slide 2</div>
          <div class="swiper-slide">Slide 3</div>
        </div>
        <!-- 如果需要分页器 -->
        <div class="swiper-pagination"></div>
        <!-- 如果需要导航按钮 -->
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
        <!-- 如果需要滚动条 -->
        <div class="swiper-scrollbar"></div>
      </div>
    </div>
  </div>
</template>

<script>

import Swiper from 'swiper/vue';

import 'swiper/css';

export default {
  name: "Swiper", 
  data() {
    return {
      numberOil:null,
      color:""


    };
  },
  methods: {},

   mounted(){
  

        var mySwiper = new Swiper('.swiper-container', {})

    }

};
</script>

<style scoped>



.swiper-container {
    width: 600px;
    height: 300px;
}
.wrapper{
  margin:30px 0; 
  height:100px;
}
</style>

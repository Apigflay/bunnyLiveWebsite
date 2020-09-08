<template>
  <div class="contectusPage">
      <h4>Tên Công Ty : BUNY LIVE</h4>

      <!-- <p v-if="language==0" class="p1">Giới thiệu sản phẩm</p> -->
      <p v-if="language==0" class="p2">Hợp tác kinh doanh:</p>
      <p v-if="language==0" class="p3">contact@bunnylive.me</p>
      <p v-if="language==0" class="p4">Email:</p>
      <p v-if="language==0" class="p5">contact@bunnylive.me</p>
      <p v-if="language==0" class="p6">Địa chỉ công ty:</p>
      <p v-if="language==0" class="p7">Lầu 1 , 624 Lạc Long Quân P5 Q11</p>
      <p v-if="language==0" class="p6">SĐT:</p>
      <p v-if="language==0" class="p7">7834732505</p>

      <!-- <p v-if="language==1" class="p1">Contect Us</p> -->
      <p v-if="language==1" class="p2">Business Cooperation:</p>
      <p v-if="language==1" class="p3">contact@bunnylive.me</p>
      <p v-if="language==1" class="p4">Feedback:</p>
      <p v-if="language==1" class="p5">contact@bunnylive.me</p>
      <p v-if="language==1" class="p6">Company Address:</p>
      <p v-if="language==1" class="p7">1 Floor ,624 Lạc Long Quân P5 Q11 HCM</p>
      <p v-if="language==1" class="p6">Telephone number:</p>
      <p v-if="language==1" class="p7">7834732505</p>


  </div>
</template>

<script>
// @ is an alias to /src
// import NavigationBar from '@/components/NavigationBar.vue'
export default {
  name: 'contectus',
  components: {

  },
  data(){
      const num =Math.floor(Math.random()*3)+1;
      return {
         strData:[]
      }
  },
  created() {  

  },    
  computed:{
    language(){
      return this.$store.getters['AllallLanguage']
    },

  },
  watch:{

  },
  methods:{
   
    
  },
  beforeMount(){
  },
  mounted() {
    //   this.swiper.slideTo(3, 1000, false)
  }
}
</script>

<style lang="scss" scoped>
.contectusPage{
  padding: 3% 10%;
  text-align: left;
  width: 80%;
  height: 94%;
  display: flex;
  flex-direction: column;
  font-size: 16px;
  line-height: 30px;
  color: #fff;
  background-image: linear-gradient(#FA5062, #F95266,#F073B2);
    p{
        text-indent: 40%;
    }
    .p1{text-indent: 0%;
        text-align: center;
        font-size: 30px;
        line-height: 140px;
    }
    .p2{
        margin-top: 100px;
    }
    .p2,.p4,.p6{
        font-size: 16px;
        line-height: 40px;
    }
    .p3,.p5,.p7{
        font-size: 24px;
        line-height: 40px;
    }
}
.icon {
    width: 35px!important;
    height: 35px!important;
}


</style>


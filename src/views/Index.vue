<template>
  <div class="indexPage">
      <div class="pageWrap">
        <!-- menu -->
        <div class="menuWrap">
            <div class="menuArea">
                <div class="menuList">
                    <img class="logo" src="../assets/imgs/logo.jpg" alt="logo">
                    <div class="menuPer" @click="goPages(index)" v-for="(item,index) in menuList[language]" :key="index">{{item}}</div>
                    <div class="menuLArea">
                        <span>Language:</span>
                        <span v-if="language==0">VN</span>
                        <span v-if="language==1">EN</span>
                        <span class="san" @click="chooseLanguage"></span>
                        <div class="languageBox" v-if="languageBox">
                            <div class="per" @click="setLanguage(0)">VN</div>
                            <div class="per" @click="setLanguage(1)">EN</div>
                        </div>
                    </div>
                    <div class="sinUpBtn" @click="goSignUp">{{loginData[language]}}</div>
                </div>
            </div>
        </div>
        <!-- swiper -->
        <div class="swiperWrap">
                <div class="topArea">
                    <div class="name">Bunny Live</div>
                    <div class="name2">{{swiperStr[language]}}</div>
                </div>
                <div class="swiperBox">
                    <el-carousel class="swiper" :interval="3000" :loop="true" height="100%">
                        <el-carousel-item class="per" style="height:100%">
                            <img class="img" src="../assets/imgs/ele-m-img-01.png" alt="">
                        </el-carousel-item>
                        <el-carousel-item class="per">
                            <img class="img" src="../assets/imgs/ele-m-img-02.png" alt="">
                        </el-carousel-item>
                        <el-carousel-item class="per">
                            <img class="img" src="../assets/imgs/ele-m-img-03.png" alt="">
                        </el-carousel-item>
                    </el-carousel>
                </div>
                <div class="btnArea">
                    <span class="img1" @click="goDown(1)"><img src="../assets/imgs/ele-btn-bg-ios.png" alt=""></span>
                    <span class="img2" @click="goDown(2)"><img src="../assets/imgs/ele-btn-bg-google.png" alt=""></span>
                </div>
        </div>
        <!-- footer -->
        <div class="footerWrap">
            copyright@2019.CONG TY TNHH BUNY
        </div>
      </div>
      <div class="introArea">
            <!-- server IP :103.127.207.137<br> -->
            Công Ty TNHH BUNNY<br>
            Địa chỉ : B01 , Tầng 1 , 624 Lạc Long Quân , Phường 5 , Quận 11<br>
            Sđt : 028.66503686<br>
            Email :bunycompany@gmail.com<br>
            Người chịu trách nhiệm nội dung: Lâm Bửu Oanh<br>
            Giấy phép MXH số 206/GP-BTTTT do Bộ TTTT cấp ngày 14/5/2020
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import NavigationBar from '@/components/NavigationBar.vue'
export default {
  name: 'Home',
  components: {

  },
  data(){
      const num =Math.floor(Math.random()*3)+1;
      return {
          menuList:[['Trang Chủ','Giới thiệu sản phẩm','','Những điều cần biết','điều khoản sử dụng','Liên lạc chúng tôi'],
          ['Home','Product Introduction ','','User Agreement','Privacy policy','Contact Us']
          ],
         swiperData:['../assets/imgs/ele-m-img-01.png','../assets/imgs/ele-m-img-02.png','../assets/imgs/ele-m-img-03.png'],
           swiperStr:['Vui mỗi ngày ','Have fun everyday'],
          languageBox:false,
          loginData:['Đăng ký','sign up'],



        mathNum:num,
      }
  },
  created() {  

  },    
  computed:{
    language(){
      return this.$store.getters['AllallLanguage']
    },
    swiper() {
        return this.$refs.mySwiper.$swiper;
    }
  },
  watch:{

  },
  methods:{
    chooseLanguage:function(){
        if(this.languageBox){
            this.languageBox=false;
        }else{
            this.languageBox=true;
        }
    },
    setLanguage:function(id){
        this.languageBox=false;
        this.$store.dispatch('SET_allLanguage',id)
    },
    goDown:function(id){
        if(id==1){
           window.location.href ="https://apps.apple.com/us/app/bunnylive/id1457545201?l=zh&ls=1"; rel="external nofollow";
        }else if(id==2){
            window.location.href ="https://play.google.com/store/apps/details?id=com.tiange.bunnylive"; rel="external nofollow";
        }
    },
    goPages:function(pageId){
      console.log(pageId)
      switch(pageId){
        case 1:
          this.$router.push({path:'/productintroduction'});
          break;
        case 2:
        //    window.location.href ="http://pay.buny.vn/"; rel="external nofollow";
          break;
        case 3:
            this.$router.push({path:'/useragressment'});
        //  this.$router.push({path:'/privacypolicy'});
          break;
        case 4:
            this.$router.push({path:'/privacypolicy'});
            // this.$router.push({path:'/useragressment'});
          break;
        case 5:
            this.$router.push({path:'/contectus'});
          break;
      }
    },
    goSignUp:function(){
        this.$router.push({path:'/signup'});
    }
  },
  beforeMount(){
  },
  mounted() {
    //   this.swiper.slideTo(3, 1000, false)
  }
}
</script>

<style lang="scss" scoped>
.indexPage{
  width: 100%;
  height: 100%;
}
.pageWrap{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}
.icon {
    width: 35px!important;
    height: 35px!important;
}
.menuWrap{//菜单栏
  width: 100%;
  height: 114px;
  background: #1e2557;
  .menuArea{
    width: 1200px;
    height: 114px;
    margin: auto;
    .menuList{
      height: 114px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      color: #fff;
      font-size: 16px;
      .logo{
          height: 80px;
          widows: 80px;
          border-radius: 10px;
      }
      .menuPer:nth-child(2){
          color: #c7495f;
      }
      .menuPer{
        cursor: pointer;
      }
      .menuPer:hover{
        color: #f16c20;
      }
      .menuLArea{
          width: 160px;
          height: 43px;
          background: #fc2c5d;
          border-radius: 10px;
          display:flex;
          align-items: center;
          justify-content: center;
          position: relative;
          .san{
            width:0;
            height:0;
            border-right:10px solid transparent;
            border-left:10px solid transparent;
            border-top:12px solid #fff;
            margin-left: 3px;
            cursor: pointer;
          }
          .languageBox{
              width: 33px;
              height: 66px;
              
              position: absolute;
              right: 12px;
              top: 43px;
              .per{
                  height: 33px;;
                  background: #f16c20;
                  line-height: 33px;
                  border-radius:2px;
                  border-radius: 50%;
                  cursor: pointer;
              }
              
          }
      }
      .sinUpBtn{
          background: #fc2c5d;
          padding: 10px 18px;
          border-radius: 10px;
          cursor: pointer;
      }
    }
  }
}
.swiperWrap{
   flex:1;
   background-image: linear-gradient(#FA5062, #F95266,#F073B2);
   display: flex;
   flex-direction: column;
   .topArea{
       width:100%;
       height: 60px;
       .name,.name2{
           height: 30px;
           line-height: 30px;
           text-align: left;
           color: #fff;
       }
       .name{
            font-size: 16px;
           text-indent: 5%;
       }
       .name2{
           text-indent: 8%;
            font-size: 20px;
       }
   }
    .swiperBox{
        flex: 1;
        .swiper{
            width: 100%;
            height: 100%;
            .el-carousel__container{
                position:static;
                // width: 100%;
                // height: 100%;
                .per{
                    width: 100%;
                    height: 100%; 
                    .img{
                        height: 100%;
                    }
                }
            }
            
        }
    }
   .btnArea{
       width:100%;
       height: 50px;
       display: flex;
       align-items: center;
       justify-content: center;
       .img1{
           height: 38px;
           width: 75px;
           background: #fff;
           border-radius: 19px;
            margin-right: 10px;
           img{
               height: 55px;
               margin-top:-7px;
           }
       }
       .img2{
           height: 38px;
           width: 75px;
           background: #fff;
           border-radius: 19px;
           margin-left: 10px;
           img{
               height: 55px;
               margin-top:-7px;
           }
       }
   }
}
.footerWrap{
    font-size: 16px;
    line-height: 60px;
}
.introArea{
    margin-bottom: 20px;
}


</style>


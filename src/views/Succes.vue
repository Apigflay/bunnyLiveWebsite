<template>
  <div class="succesPage">
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
        <!-- succes -->
        <div class="succesWrap">
            <div class="succesArea">
                <img class="success" src="@/assets/imgs/success.png" alt="">
                <p class="p">Thông tin đã điền đầy đủ, vui lòng tải APP để hoàn thành bước cuối cùng</p>
                <div class="suDownArea">
                    <div class="div" @click="goDown(1)"><img class="btn" src="@/assets/imgs/ele-btn-bg-ios.png" alt=""></div>
                    <div class="div" @click="goDown(2)"><img class="btn" src="@/assets/imgs/ele-btn-bg-google.png" alt=""></div>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'Succes',
  components: {

  },
  data(){
      const num =Math.floor(Math.random()*3)+1;
      return {
            menuList:[['Trang Chủ','Giới thiệu sản phẩm','','điều khoản sử dụng','Những điều cần biết','Liên lạc chúng tôi'],
                ['Home','Product Introduction ','','Privacy policy','User Agreement','Contact Us']
            ],
            swiperData:['../assets/imgs/ele-m-img-01.png','../assets/imgs/ele-m-img-02.png','../assets/imgs/ele-m-img-03.png'],
            swiperStr:['Vui mỗi ngày ','Have fun everyday'],
            languageBox:false,
            loginData:['Đăng nhập','sign up'],
            






        mathNum:num,
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
    goPages:function(pageId){
      console.log(pageId)
      switch(pageId){
        case 0:
          this.$router.push({path:'/'});
          break;
        case 1:
          this.$router.push({path:'/productintroduction'});
          break;
        case 2:
        //    window.location.href ="http://pay.buny.vn/"; rel="external nofollow";
          break;
        case 3:
         this.$router.push({path:'/privacypolicy'});
          break;
        case 4:
            this.$router.push({path:'/useragressment'});
          break;
        case 5:
            this.$router.push({path:'/contectus'});
          break;
      }
    },
    goSignUp:function(){
        this.$router.push({path:'/signup'});
    },

    goNext:function(){
        if(this.p1==true&&this.p2==true&&this.p4==true&&this.p5==true&&this.p6==true&&this.p7==true&&this.p8==true){
            this.$message('Thông tin đã điền đầy đủ, vui lòng tải APP để hoàn thành bước cuối cùng');
            
        }else{
            this.$message('Vui lòng điền lại');
        }
        
    },
    goDown:function(id){
        if(id==1){
           window.location.href ="https://apps.apple.com/us/app/bunnylive/id1457545201?l=zh&ls=1"; rel="external nofollow";
        }else if(id==2){
            window.location.href ="https://play.google.com/store/apps/details?id=com.tiange.bunnylive"; rel="external nofollow";
        }
    },

  },
  beforeMount(){
  },
  mounted() {
    //   this.swiper.slideTo(3, 1000, false)
  }
}
</script>

<style lang="scss" scoped>
.succesPage{
  width: 100%;
  height: 100%;
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
        //   color: #c7495f;
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
.succesWrap{
    width: 100%;
    .succesArea{
        min-height: 400px;
        width: 1200px;
        margin: auto;
        .success{
            margin-top: 250px;
            height: 50px;
            width: 50px;
        }
        .p{
            line-height: 50px;
        }
        .suDownArea{
            display: flex;
            justify-content: center;
            margin-top: 20px;
            .div{
                height: 38px;
                width: 75px;
                border-radius: 19px;
                height: 38px;
                position: relative;
                background: #cecece;
                margin:0 20px;
                cursor: pointer;
                .btn{
                    position: absolute;
                    width: 50px;
                    top: -4px;
                    left: 12px;
                    height: 50px;
                }
            }
        }
    }
}

</style>


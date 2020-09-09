<template>
  <div class="indexPage">
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
        <!-- sign up -->
        <div class="signWrap">
            <div class="signArea">
                <!-- 1 姓名 -->
                <div class="per1 per">
                    <span class="lable">Họ và tên :</span>
                    <el-input class="lable_input" v-model.trim="inputName" maxlength='30' placeholder="" @input="getInputMsg(1)"></el-input>
                </div>
                <p class="per1 per_p" v-if="p1==false">Vui lòng điền lại</p>
                <!-- 2 生日-->
                <div class="per2 per">
                    <span class="lable">Ngày tháng năm sinh :</span>
                    <el-select v-model="inputBirth1" placeholder="Ngày" class="ri">
                        <el-option
                        v-for="(item,index) in 31"
                        :key="index"
                        :label="item"
                        size="mini"
                        :value="item">
                        </el-option>
                    </el-select>
                    --
                    <el-select v-model="inputBirth2" placeholder="Tháng" class="yue">
                        <el-option
                        v-for="(item,index) in 12"
                        :key="index"
                        :label="item"
                        :value="item">
                        </el-option>
                    </el-select>
                    --
                    <el-date-picker
                        format="yyyy"
                        v-model="inputBirth3"
                        type="year"
                        placeholder="Năm">
                    </el-date-picker>

                    

                    <!-- <el-date-picker
                    format="dd-MM-yyyy"
                    v-model="inputBirth"
                    type="date"
                    placeholder="" @blur="getInputMsg(2)">
                    </el-date-picker> -->
                </div>
                <p class="per2 per_p" v-if="p2==false">Vui lòng điền lại</p>
                <!-- 3 证件类型-->
                <div class="per3 per">
                    <span class="lable">loại chứng chỉ :</span>
                    <el-select v-model="input3" placeholder=""  @blur="getInputMsg(3)">
                        <el-option label="Thẻ căn cước CMND" value="Thẻ căn cước CMND"></el-option>
                        <el-option label="hộ chiếu" value="hộ chiếu"></el-option>
                    </el-select>
                </div>
                <!-- <p class="per3 per_p" v-if="p3==false">Thông tin tên quá dài! Vui lòng điền lại</p> -->
                <!-- 4 证件号-->
                <div class="per4 per">
                    <span class="lable">Số :</span>
                    <el-input class="lable_input" v-model.trim="input4" placeholder="" maxlength='30' @input="getInputMsg(4)"></el-input>
                </div>
                <p class="per4 per_p" v-if="p4==false">Vui lòng điền lại</p>
                <!-- 5 签发日期-->
                <div class="per5 per">
                    <span class="lable">Ngày cấp :</span>

                    <el-select v-model="input51" placeholder="Ngày" class="ri">
                        <el-option
                        v-for="(item,index) in 31"
                        :key="index"
                        :label="item"
                        size="mini"
                        :value="item">
                        </el-option>
                    </el-select>
                    --
                    <el-select v-model="input52" placeholder="Tháng" class="yue">
                        <el-option
                        v-for="(item,index) in 12"
                        :key="index"
                        :label="item"
                        :value="item">
                        </el-option>
                    </el-select>
                    --
                    <el-date-picker
                        format="yyyy"
                        v-model="input53"
                        type="year"
                        placeholder="Năm">
                    </el-date-picker>

                    <!-- <el-date-picker key="2"
                    v-model="input51"
                    type="date"
                    placeholder="" @blur="getInputMsg(5)">
                    </el-date-picker> -->
                </div>
                <p class="per5 per_p" v-if="p5==false">Vui lòng điền lại</p>
                <!-- 6 签发地-->
                <div class="per5 per">
                    <span class="lable">Nơi cấp :</span>
                    <el-input class="lable_input" v-model.trim="input6" maxlength='30' placeholder="" @input="getInputMsg(6)"></el-input>
                </div>
                <p class="per5 per_p" v-if="p6==false">Vui lòng điền lại</p>
                <!-- 7 email-->
                <div class="per5 per">
                    <span class="lable">email :</span>
                    <el-input class="lable_input" v-model.trim="input7" placeholder="" @input="getInputMsg(7)"></el-input>
                </div>
                <p class="per5 per_p" v-if="p7==false">Vui lòng điền lại</p>
                <!-- 8 地址-->
                <div class="per5 per">
                    <span class="lable">Địa chỉ :</span>
                    <el-input class="lable_input" v-model.trim="input8" placeholder="" @input="getInputMsg(8)"></el-input>
                </div>
                <p class="per5 per_p" v-if="p8==false">Vui lòng điền lại</p>
                 <!-- 9 电话-->
                <div class="per5 per">
                    <span class="lable">SĐT :</span>
                    <el-input class="lable_input" maxlength='10' v-model.trim="input9" placeholder="" @input="getInputMsg(9)"></el-input>
                </div>
                <p class="per5 per_p" v-if="p9==false">Vui lòng điền lại</p>
                <!-- 10 -->
                <div class="nextBtn" @click="goNext">Bước tiếp theo</div>
            </div>
        </div>
        <!--  -->
        <el-dialog class="dialog"
            title=" Mẹo"
            :visible.sync="centerDialogVisible"
            width="30%"
            center>
            <div class="dialogDiv">
                Họ và tên :{{this.inputName}}
            </div>
            <div class="dialogDiv">
                Ngày tháng năm sinh :{{this.inputBirth1<10?'0'+this.inputBirth1:this.inputBirth1}}--{{this.inputBirth2<10?'0'+this.inputBirth2:this.inputBirth2}}--{{this.year1}}
            </div>
            <div class="dialogDiv">
                loại chứng chỉ :{{this.input3}}
            </div>
            <div class="dialogDiv">
                Số :{{this.input4}}
            </div>
            <div class="dialogDiv">
                Ngày cấp :{{this.input51<10?'0'+this.input51:this.input51}}--{{this.input52<10?'0'+this.input52:this.input52}}--{{this.year2}}
            </div>
            <div class="dialogDiv">
                Nơi cấp :{{this.input6}}
            </div>
            <div class="dialogDiv">
                email :{{this.input7}}
            </div>
            <div class="dialogDiv">
                Địa chỉ :{{this.input8}}
            </div>
            <div class="dialogDiv">
                SĐT :{{this.input9}}
            </div>
            <!-- <span>需要注意的是内容是默认不居中的</span> -->
            <span slot="footer" class="dialog-footer">
                <el-button @click="centerDialogVisible = false">hủy bỏ</el-button>
                <el-button type="primary" @click="goPageSuccess">xác nhận</el-button>
            </span>
        </el-dialog>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'SignUp',
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
            inputName:'',//name 
            p1:true,//false  错误  true 不显示
            inputBirth1:'',//生日 日
            inputBirth2:'',//生日 月
            inputBirth3:'',//生日 年
            p2:true,//false  错误  true 不显示
            input3:'Thẻ căn cước CMND',//证件类型
            p3:true,//false  错误  true 不显示
            input4:'',//证件号
            p4:true,//false  错误  true 不显示
            input51:'',//签发日期 日
            input52:'',//签发日期 月
            input53:'',//签发日期 年
            p5:true,//false  错误  true 不显示
            input6:'',//签发地
            p6:true,//false  错误  true 不显示
            input7:'',//Email
            p7:true,//false  错误  true 不显示
            input8:'',//地址
            p8:true,//false  错误  true 不显示
            input9:'',//地址
            p9:true,//false  错误  true 不显示

            centerDialogVisible: false,//dialog






        mathNum:num,
      }
  },
  created() {  

  },    
  computed:{
    language(){
      return this.$store.getters['AllallLanguage']
    },
    allIs(){
        return this.inputName!=''&&this.inputBirth1!=''&&this.inputBirth2!=''&&this.inputBirth3!=''&&this.input4!=''&&this.input51!=''&&this.input6!=''&&this.input7!=''&&this.input8!=''&&this.input9!='';
    },
    year1(){
        var y = new Date(this.inputBirth3).getFullYear()
        return y
    },
    year2(){
        var y = new Date(this.input53).getFullYear()
        return y
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
    getInputMsg:function(id){
        // console.log(id)
        if(id==1){
            if(this.inputName.length>5){
                this.p1=true;
            }else{
                this.p1=false;
            }
        }else if(id==2){
             if(this.inputBirth==''){
                this.p2=false;
            }else{
                this.p2=true;
            }
        }else if(id==3){
            // console.log(this.input3)
            if(this.input3==''){
                this.p3=false;
            }else{
                this.p3=true;
            }
        }else if(id==4){
            // console.log(this.input4)
            if(this.input4.length<12&&this.input4.length>8){
                this.p4=true;
            }else{
                this.p4=false;
            }
        }
        else if(id==5){
            // console.log(this.input5=='')
            if(this.input5==''){
                this.p5=false;
            }else{
                this.p5=true;
            }
        }
        else if(id==6){
            // console.log(this.input6)
            if(this.input6.length<31&&this.input6.length>6){
                this.p6=true;
            }else{
                this.p6=false;
            }
        }
        else if(id==7){
            // console.log(this.input7)
            var reg = new RegExp("^[a-z0-9A-Z]+[- | a-z0-9A-Z . _]+@([a-z0-9A-Z]+(-[a-z0-9A-Z]+)?\\.)+[a-z]{2,}$"); 
            var test =reg.test(this.input7);
            if(test==true){
                this.p7=true;
            }else{
                this.p7=false;
            }
        }
        else if(id==8){
            // console.log(this.input8)
            if(this.input8.length<31&&this.input8.length>6){
                this.p8=true;
            }else{
                this.p8=false;
            }
        }else if(id==9){
            // console.log(this.input9)
            if(this.input9.length<10){
                this.p9=false;
            }else{
                this.p9=true;
            }
        }
    },
    goNext:function(){
        // console.log(this.year1)
        // console.log(this.year2)
        // console.log(this.allIs)
        // console.log(this.inputName,'----------1')
        // console.log(this.inputBirth1,this.inputBirth2,this.inputBirth3,'----------2')
        // console.log(this.input3,'----------3')
        // console.log(this.input4,'----------4')
        // console.log(this.input51,this.input52,this.input53,'----------5')
        // console.log(this.input6,'----------6')
        // console.log(this.input7,'----------7')
        // console.log(this.input8,'----------8')
        if(this.p1==true&&this.p2==true&&this.p4==true&&this.p5==true&&this.p6==true&&this.p7==true&&this.p8==true&&this.p9==true&&this.allIs==true){
            
            this.centerDialogVisible=true;
            // this.$message('Thông tin đã điền đầy đủ, vui lòng tải APP để hoàn thành bước cuối cùng');
            // this.$router.push({path:'/succes'});

        }else{
            this.$message('Vui lòng điền lại');
        }
        
    },
    goPageSuccess:function(){
        this.centerDialogVisible=false;
        this.$message('Thông tin đã điền đầy đủ, vui lòng tải APP để hoàn thành bước cuối cùng');
        this.$router.push({path:'/succes'});

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
.signWrap{
    width: 100%;
    .signArea{
        padding:50px 0;
        width: 1200px;
        margin: auto;
        min-height: 300px;
        .per{
            display: flex;
            align-items: center;
            height: 40px;
            margin-top: 5px;
            .lable{
                width: 250px;
                height: 40px;
                text-align: right;
                font-size: 18px;
                line-height: 40px;
                margin-right: 15px;
                margin-left: 180px;
            }
            .lable_input{
                width: 300px;
                height: 40px;
            }
            .ri,.yue{
                width: 100px;
            }
        }
        .per_p{
            height: 24px;
            color: #fe4761;
            font-size: 16px;
            line-height: 24px;
            text-align: left;
            text-indent: 444px;
        }
        .nextBtn{
            width: 300px;
            height: 50px;
            background: #fc2c5d;
            border-radius: 10px;
            margin: auto;
            margin-top: 50px;
            color: #fff;
            line-height: 50px;
            text-align: center;
        }
    }
}
.dialog{
    .dialogDiv{
        line-height: 30px;
        font-size: 16px;
    }
}
</style>


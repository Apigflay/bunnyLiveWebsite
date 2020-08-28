// <template>
//   <div class="homePage">
//       <!-- nav -->
//       <NavigationBar :language="language" @getChirldrenMethod="getChirldrenMethod"></NavigationBar>
//       <!-- menu -->
//       <div class="menuWrap">
//           <div class="menuArea">
//               <div class="menuTip">
//                 <p>章鱼🐙</p>
//                 <p>一个人.</p>
//               </div>
//               <div class="menuList">
//                 <div class="menuPer" @click="goPages(1)">首页HOME</div>
//                 <div class="menuPer" @click="goPages(2)">博客BLOG</div>
//                 <div class="menuPer" @click="goPages(3)">视频VIDEO</div>
//                 <div class="menuPer" @click="goPages(4)">音乐MUSIC</div>
//                 <div class="menuPer" @click="goPages(5)">游戏GAMES</div>
//                 <div class="menuPer" @click="goPages(6)">终端ADMIN</div>
//                 <div class="menuPer" @click="goPages(7)">敬请期待...</div>
//                 <div class="menuPer" @click="goPages(8)">作者ABOUT ME</div>
//               </div>
//           </div>
//       </div>
//       <!-- moon -->
//       <Moon></Moon>
//       <!-- introduction -->
//       <div class="introductionWrap">
//           <div class="introductionArea">
//               <h2 class="intro_h2">My Blog</h2>
//               <div class="intro_underline"></div>
//               <p class="p">我的博客，承载了我的学习之路。</p>
//               <ul class="ul">
//                 <li class="li">
//                   <svg class="icon" aria-hidden="true">
//                     <use xlink:href="#icon-xinxiduanxinxiaoxitixingyoujiansixinyouxiang"></use>
//                   </svg>
//                   <span>283251605@qq.com</span>
//                 </li>
//                 <li class="li">
//                   <svg class="icon" aria-hidden="true">
//                     <use xlink:href="#icon-weizhi1"></use>
//                   </svg>
//                   <span>Xihu District, Hangzhou, China</span>
//                 </li>
//                 <li class="li">
//                   <svg class="icon" aria-hidden="true">
//                     <use xlink:href="#icon-AlphaXtubiao-"></use>
//                   </svg>
//                   <span>283251605</span>
//                 </li>
//               </ul>
//           </div>
//       </div>
//       <!-- 留言板 -->
//       <MessageBoard></MessageBoard> 
//       <DrawingBoard></DrawingBoard>
      
//       <!-- <span @click="texttoast(1)"> hahhhh</span> -->
//       <!-- <span @click="texttoast(2)"> none</span> -->
//       <KeepOnRecord></KeepOnRecord>  
//       <Toast></Toast>
//   </div>
// </template>

// <script>
// // @ is an alias to /src
// import NavigationBar from '@/components/NavigationBar.vue'
// import HelloWorld from '@/components/HelloWorld.vue'
// import KeepOnRecord from '@/components/KeepOnRecord.vue'
// import Moon from '@/components/Moon.vue'
// import MessageBoard from '@/components/MessageBoard.vue'
// import DrawingBoard from '@/components/DrawingBoard.vue' 
// export default {
//   name: 'Home',
//   components: {
//     KeepOnRecord,
//     NavigationBar,
//     Moon,
//     MessageBoard,
//     DrawingBoard
//   },
//   data(){
//       const num =Math.floor(Math.random()*3)+1;
//       return {
//         mathNum:num,
//       }
//   },
//   created() {
//   },
//   computed:{
//     language(){
//       return this.$store.getters['AllallLanguage']
//     }
//   },
//   watch:{

//   },
//   methods:{
//     getChirldrenMethod:function(msg){
//       this.$store.commit['set_allLanguage',msg]
//     },
//     texttoast:function(id){
//       if(id==1){
//         this.$Toast(true,'哈哈哈')
//       }else if(id==2){
//         this.$Toast(false)
//       }
//     },
//     goPages:function(pageId){
//       console.log(pageId)
//       switch(pageId){
//         case 1:
//           this.$router.push({path:'/'});
//           break;
//         case 2:
//           this.$router.push({path:'/editblog'});
//           break;
//       }
//     }
//   },
//   beforeMount(){
//   },
//   mounted(){
//   },
// }
// </script>

// <style lang="scss">
// .homePage{
//   width: 100%;
//   height: 100%;
// }
// .icon {
//     width: 35px!important;
//     height: 35px!important;
// }
// .menuWrap{//菜单栏
//   width: 100%;
//   height: 77px;
//   background: #fff;
//   .menuArea{
//     width: 1200px;
//     height: 77px;
//     margin: auto;
//     display: flex;
//     justify-content: space-between;
//     .menuTip{
//       text-align: left;
//       p:nth-child(1){
//         font-size: 24px;
//         color: #be5000;
//         line-height: 28px;
//         margin-top: 16px;
//         cursor: pointer;
//       }
//       p:nth-child(1):hover{
//         text-decoration: underline;
//       }
//       p:nth-child(2){
//         font-size: 12px;
//         line-height: 16px;
//       }
//     }
//     .menuList{
//       height: 70px;
//       display: flex;
//       align-items: center;
//       justify-content: space-between;
//       .menuPer{
//         margin-left: 30px;
//         cursor: pointer;
//       }
//       .menuPer:hover{
//         color: #f16c20;
//       }
//     }
//   }
// }
// .introductionWrap{//介绍
//   width: 100%;
//   background: #fff;
//   .introductionArea{
//      width: 1200px;
//      margin: auto;
//      padding: 90px 0px 60px 0px;
//      .intro_h2{
//        font-size: 40px;
//        line-height: 50px;
//        margin-bottom: 20px;
//      }
//      .intro_underline{
//         width: 80px;
//         height: 2px;
//         background: #f16c20;
//         margin: auto;
//      }
//      .p{
//        margin-top: 20px;
//        font-size: 16px;
//      }
//      .ul{
//        width: 100%;
//        height: 219px;
//        display: flex;
//        align-items: center;
//        justify-content: center;
//        .li{
//          display: flex;
//          font-weight: 600;
//          flex-direction: column;
//          align-items: center;
//          justify-content: space-around;
//          width: 230px;
//          span{
//            margin-top: 30px;
//          }
//        }
//        .li:nth-child(2){
//          margin:0 110px;
//        }
//        .li span:hover{
//          color:#f16c20;
//        }
//      }

//   }
// }
// </style>


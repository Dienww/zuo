<template>
  <div class="home">
    <!--中间部分-->
    <div class="home_content">
      <!--左边的内容-->
      <div class="hc_left">
        <Topic></Topic>
        <!--设计展示-->
        <div class="content">
          <!--头部-->
          <div class="designNav">
            <div class="dn_left">
              <div class="all">
                <img @click="navAll" src="../../assets/zuoindex/blacknav.png" alt="">
                <span class="quanbu" @click="navAll">全部</span>
                <img @click="navAll" src="../../assets/zuoindex/darrow.png" alt="">
                <div class="allNav" v-show="isAllNav">
                  <!--箭头-->
                  <div class="square"></div>
                  <!--全部下拉列表-->
                  <ul class="xiala">
                    <li >
                      <a href="">
                        <img src="../../assets/zuoindex/graynav.png" alt="">
                        <span>全部</span>
                      </a>
                    </li>
                    <li  v-for="arrAll in this.navArr">
                      <!--导航循环-->
                      <a href="">
                        <div class="navcolor" :style="{backgroundColor: 'rgb('+ arrAll.color +')'}"></div>
                        <span>{{arrAll.name}}</span>
                      </a>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
            <!--选框-->
            <div class="dn_right">
              <div class="dei">
                <a class="a1" >
                  <img v-show="blueisShow" class="ckeckblue" src="../../assets/zuoindex/checkblue.png" @click="chooseBlue" alt="">
                  <img v-show="!blueisShow" src="../../assets/zuoindex/checkgray.png" @click="chooseBlue" alt="">
                  <span class="span1">好设计</span>
                </a>
                <a class="a2">
                  <img v-show="redisShow" class="ckeckred" ref="choose2" src="../../assets/zuoindex/checkred.png" @click="chooseRed" alt="">
                  <img v-show="!redisShow" src="../../assets/zuoindex/checkgray.png" @click="chooseRed" alt="">
                  <span class="span2">坏设计</span>
                </a>
              </div>
            </div>
          </div>

          <!--具体展示部分-->
          <div class="designShow">
            <!--for循环-->
            <div v-for="(myArr,index) in this.contentArr" class="myDesign" ref="designBox">
              <!--上传者信息-->
              <div class="showTop">
                <div class="st_left">
                  <!--用户信息-->
                  <div class="dsUser">
                    <!--头像-->
                    <div class="userImg">
                      <div class="myUserImg">
                        <img :src="myArr.owner.avatar" alt="">
                      </div>
                      <div class="myc">C</div>
                    </div>
                    <div class="userName">{{myArr.owner.nickname}}</div>
                  </div>
                </div>
                <div class="st_right">
                  <img class="circle deImg" src="../../assets/zuoindex/circle.png" alt="">
                  <span>{{myArr.likeCount}}个赞同</span>
                  <a href="">
                    <!--分享-->
                    <img class="share deImg" src="../../assets/zuoindex/share.png" alt="">
                    <!--举报-->
                    <img class="report deImg" src="../../assets/zuoindex/omit.png" alt="">
                  </a>
                </div>
              </div>
              <div class="showBody">
                <div class="feedImg">
                  <div class="feedImgMb"></div>
                  <img :src="myArr.postImage.url" alt="" class="showImg">
                  <a class="like" href="">
                    <!--赞同的圆圈定位-->
                    <div class="lBig" :style="{left:myArr.haloCenterRatio.width_ratio*100+'%',top:myArr.haloCenterRatio.height_ratio*100+'%'}">
                      <div class="zanFont">
                        <span class="bigFont">赞同</span>
                        <br>
                        <span class="smallFont">这个态度</span>
                      </div>
                      <div class="lSmall">
                      </div>
                    </div>
                  </a>
                </div>
                <div class="feedContent">
                  <div class="feedText">{{myArr.postDescription}}</div>
                  <div class="feedTags">
                    <!--设计所属分类标签-->
                    <a href="">
                      <span class="feesSpan1" :style="{backgroundColor:myArr.sceneTag.color}"></span>
                      <span>{{myArr.sceneTag.name}}</span>
                    </a>
                    <a v-for="tag in myArr.tags" href="">
                      <img src="../../assets/zuoindex/gray.png" alt="">
                      <span>{{tag}}</span>
                    </a>
                  </div>
                  <div class="feedInto">
                    <div class="fiTop">
                      <a href="">{{myArr.commentedCount}}条评论</a>&nbsp;&nbsp;&nbsp;&nbsp;
                      <a href="">更多评论…</a>
                    </div>
                    <!--互动评论-->
                    <div class="fiFoot">
                      <div class="fiFootbox" v-for="(small,index2) in myArr.comments">
                        <p class="fip1">
                          <span v-html="small.author.nickname" :ref="'index'+index2">{{small.author.nickname}}</span>
                          <span>-</span>
                          <span v-html="small.text">{{small.text}}</span>
                        </p>
                        <div class="fip2box">
                          <p class="fip2">{{small.timeAgo}}</p>
                          <div class="interact">
                            <div class="inter1"> <a @click="reply(index,small.author.nickname)">回复</a></div>
                            <div class="inter2">
                              <span>点亮</span>
                              <span class="inter2sp2">{{small.likeNumber}}</span>
                              <img src="../../assets/zuoindex/light.png" alt="">
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                  <!--用户评论-->
                  <div class="feedAdd">
                    <div class="inputText">
                      <textarea name="" id="" placeholder="写下你的评论…"  @click="review(index)" ref="rev"></textarea>
                      <div class="revise" v-show="isReviseShow" ref="closeRev">
                        <a @click="cancel(index)">取消</a>
                        <a class="a1">评论</a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>


      <!--热门标签-->
      <div class="hc_right">
        <div class="dsright"  ref="right1">
          <IndexRight @passdown="passdown1" :class="{dsright1:isDsr}" class="inright"></IndexRight>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  import Topic from '../index/Topic.vue'
  import IndexRight from '../index/IndexRight.vue'

  export default {
    name: 'IndexContent',
    components: {
      Topic,
      IndexRight
    },
    data() {
      return {
        contentArr: [],
//      控制评论框
        isReviseShow:false,
        isAllNav:false,
        navArr:[
          {name:'日用',color:'228, 204, 169'},
          {name:'公共',color:'161, 228, 64'},
          {name:'关爱',color:'255, 71, 71'},
          {name:'家居',color:'88, 0, 24'},
          {name:'时尚',color:'157, 0, 255'},
          {name:'美食',color:'255, 150, 0'},
          {name:'数码',color:'33, 140, 124'},
          {name:'视觉',color:'255, 234, 0'},
          {name:'空间',color:'0, 191, 243'},
        ],
        blueisShow:true,
        redisShow:true,
        isDsr :false
      }
    },
    mounted() {
      var _this = this;
//      axios.get('api/web_hot_posts.').then
      axios.get('api/web_hot_posts.json').then
      (function (res) {
        _this.contentArr = res.data.posts;
      });
//      鼠标滚轮监听
      window.addEventListener('scroll', this.onScroll);
    },
    methods:{
//    用户评论下拉列表
      review:function (index) {
       this.$refs.rev[index].style.minHeight = 100+'px';
       this.$refs.closeRev[index].style.display = "block";
      },
//    取消列表收回
      cancel:function (index) {
        this.$refs.rev[index].style.minHeight= 50+'px';
        this.$refs.closeRev[index].style.display = "none";
      },
      navAll:function () {
        this.isAllNav = !this.isAllNav
      },
      passdown1:function () {
        this.$emit('pass-c-down')
      },
//    好设计坏设计必须选中一个的判断函数
      chooseBlue:function () {
        if(this.redisShow == false){
          alert('必须选择一个哦(づ｡◕‿‿◕｡)づ');
          return;
        }else {
          this.blueisShow = !this.blueisShow;
        }
      },
      chooseRed:function () {
        if(this.blueisShow == false){
          alert('必须选择一个哦(づ｡◕‿‿◕｡)づ');
          return;
        }else {
          this.redisShow = !this.redisShow
        }
      },
//     回复
      reply:function (index,b) {
        this.$refs.rev[index].value = '@'+ b;
      },
      onScroll:function () {
        let scrolled = '';
//      获取页面滚动距离
        scrolled = document.documentElement.scrollTop || document.body.scrollTop;
//        console.log(scrolled);
        if (scrolled >= 500){
          this.isDsr=true;
        }
        if(scrolled < 500){
          this.isDsr=false;
        }
      }
    }
  }
</script>

<style scoped>
  .home {
    width: 100%;
    background-color: #f6f6f6;
  }
  .home_content {
    width: 790px;
    margin: 0 auto;
    position: relative;
    display: flex;
    justify-content: space-between;
    padding-top: 30px;
  }
  .home_content .hc_left {
    width: 540px;
    padding-bottom: 30px;
  }

  /*设计讨论区*/
  .content {
    width: 100%;
  }

  /*单选栏*/
  .allNav ul li{
    list-style: none;
  }
  .allNav ul li a{
    text-decoration: none;
    color: #a6a7a7;
    font-weight: 500;
    text-align: center;
  }
  .designNav {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin-bottom: 18px;
  }
  .quanbu{
    margin: 0 5px;
  }
  .dn_left .all {
    display: flex;
    align-items: center;
    position: relative;
  }
  .dn_left .all img {
    width: 16px;
  }
  /*方块*/
  .square{
    position: absolute;
    width: 13px;
    height: 13px;
    border-left: 1px solid #ccc;
    border-top: 1px solid #ccc;
    border-right: 0;
    border-bottom: 0;
    background-color: #fff;
    -webkit-transform: rotate(45deg);
    transform: rotate(45deg);
    margin-left: -5px;
    top: 30px;
    left: 48%;
    z-index: 6;
  }
  .navcolor{
    width: 8px;
    height: 8px;
    border-radius: 50%;
  }
  .xiala{
    top: 35px;
    min-width: 100px;
    padding: 5px 10px;
    position: absolute;
    left: -15px;
    background-color: white;
    z-index: 5;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  .xiala li a{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 15px;
    text-decoration: none;
    color: #a6a7a7;
    font-weight: 500;
    text-align: center;
    border-radius: 4px;
  }
  .xiala li a:hover{
    background-color: #f5f5f5;
  }
  .xiala li{
    border-bottom: 1px solid #ececec;
    padding: 5px 0;
  }
  .dn_right {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .dn_right a {
    color: #959697;
    margin-left: 15px;
    text-decoration: none;
  }
  .dn_right .a1 .check1 {
    color: #1fd7e2;
  }
  .dn_right .a2 .check2 {
    color: #ff3622;
  }
  .dn_right span {
    padding-left: 10px;
  }
  .dn_right img{
    width: 16px;
    height: 16px;
  }
  /*左边的内容展示*/
  .designShow {
    width: 100%;
  }
  .myDesign {
    margin-bottom: 30px;
    border-radius: 5px;
    overflow: hidden;
  }
  .myDesign:hover{
    box-shadow: 3px 0 5px 0 #eee;
  }
  .showBody{

    background-color: white;
  }
  .showTop {
    padding: 10px 18px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: white;
  }
  .dsUser {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .userImg {
    position: relative;
    display: flex;
  }
  .myUserImg {
    width: 40px;
    height: 40px;
    border-radius: 20px;
    overflow: hidden;
  }
  .myc {
    background-color: #00dae1;
    color: white;
    text-align: center;
    width: 16px;
    height: 16px;
    font-size: 12px;
    border-radius: 10px;
    position: relative;
    left: -50px;
    top: 0;
  }
  .deImg {
    width: 16px;
    height: 16px;
    margin: 10px;
  }
  .st_right {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  /*展示区*/
  .feedImg {
    position: relative;
    width: 100%;
    overflow: hidden;
    height: 540px;
  }
  .feedImgMb{
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: black;
    opacity: 0.2;
    display: none;
  }
  .feedImg:hover .feedImgMb{
    display:block;
  }
  .feedImg:hover .zanFont{
    transition: 0.5s;
    opacity: 1;
  }
  .feedImg:hover .lBig{
    transition: 0.2s;
    transform: scale(1.1);
    border:5px solid #1fd7e2;
  }
  .zanFont{
    color: white;
    text-align: center;
    position: absolute;
    top:20%;
    left: 26%;
    opacity: 0;
  }
  .bigFont{
    font-size: 24px;
  }
  .smallFont{
    font-size: 14px;
  }
  /*圆圈定位*/
  .lBig {
    border: 3px solid #1fd7e2;
    border-radius:50%;
    width: 120px;
    height: 120px;
    position: absolute;
    margin-left: -60px;
    margin-top: -60px;

  }
  .lSmall {
    width: 120px;
    height: 120px;
    border-radius: 100px;
    position: absolute;
    left: -3px;
    top: -3px;
    animation: fangda 1s;
    animation-iteration-count: infinite;
    background-color: rgba(31, 217, 255,.2);
    opacity: 0.2;
    border: 1px solid #1fd7e2;
  }
  .feedContent {
    padding: 18px 25px 0 25px;
    font-size: 14px;
  }
  .feedText {
    line-height: 22px;
    color: #595c5d;
  }
  .feedTags {
    line-height: 22px;
    padding: 18px 0;
    color: #595c5d;
    border-bottom: 1px solid #ececec;
    display: flex;
    flex-direction: row;
  }
  .feedTags a {
    color: #a6a7a7;
    display: flex;
    align-items: center;
    padding-right: 15px;
  }
  .feedTags a img {
    width: 16px;
  }
  .feedInto {
    padding-bottom: 9px;
    align-items: center;
    line-height: 20px;
    border-bottom: 1px solid #ececec;
  }
  .feedInto .fiTop {
    padding: 18px 0;
    display: flex;
    -ms-flex-align: center;
    align-items: center;
    line-height: 20px;
  }
  .feedInto .fiFoot {
    font-size: 12px;
  }
  .feedInto a {
    color: #a6a7a7;
  }
  .feedInto .fiFoot .fip1 {
    margin-bottom: 0;
  }
  .feedInto .fiFoot .fip1 span {
    font-weight: bold;
    padding-right: 3px;
  }
  .feedInto .fiFoot .fip2box{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .feedInto .fiFoot .fip2 {
    padding-top: 3px;
    color: #a6a7a7;
  }
  .feedInto .fiFoot .fip2box .interact{
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .inter1{
    margin-right: 18px;
    display: none;
  }
  .inter2{
    display: flex;
    align-items: center;
    color: #a1a2a3;
    cursor: pointer;
  }
  .inter2sp2{
    padding: 3px;
  }
  .inter2 img{
    width: 16px;
    height: 16px;
  }
  .feedAdd {
    width: 100%;
  }
  /*类型前的点*/
  .feesSpan1{
    width: 10px;
    height: 10px;
    border-radius: 50%;
    margin-right: 5px;
  }
  .inputText textarea {
    min-height: 50px;
    width: 100%;
    outline: 0;
    border: none;
    padding: 18px 0 18px 2px;
    font-size: 14px;
    line-height: 20px;
  }
  .revise {
    display: none;
    padding: 15px 0;
  }
  .revise a {
    color: black;
  }
  .revise .a1{
    float: right;
  }
  .fiFootbox{
    border-radius: 5px;
    padding: 5px;
    box-sizing: border-box;
  }
  .fiFootbox:hover{
    background-color: #f7f7f8;
  }
  .fiFootbox:hover .inter1{
    display: block;
  }

/*右边*/
  .hc_right{
    position: relative;
  }
  .dsright{
    width: 223px;
    position: relative;
  }
  .dsright1{
    position: fixed;
    bottom: 160px;
  }
  /*.inright{*/
  /*}*/
  /*动画*/
  /*放大*/
  @keyframes fangda {
    0% {
      transform: scale(1);
      opacity:1;
    }
    100%{
      transform: scale(1.5);
      opacity:0;
   }
  }
  /*赞同出现*/
</style>

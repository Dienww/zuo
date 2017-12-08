<template>
  <div class="wrap">
    <zuo-nav @pass="myLogin" @passPost="myPost" @passDownOpen="openMyDown" :isActive="myact"></zuo-nav>
    <index-top @pass-c-post="myPost" ></index-top>
    <index-content @pass-c-down="openMyDown"></index-content>
    <Login v-show="isLogin" @pass1="myLogin" @pass2="skipMyPost" @openPl="skipPassLogin"></Login>
    <PassLogin v-show="isPassLogin" @passPost="openPost"></PassLogin>
    <Post v-show="isPost" @passPost1="myPost" @passPost2="skipMyLogin"></Post>
    <down-load v-show="isDown" @passDown="closeDown"></down-load>
    <magnify></magnify>

  </div>
</template>

<script>
  import MyIndex from '../../components/index/Index';
  import ZuoNav from '../../components/zuonav/ZuoNav';
  import IndexTop from "../../components/index/IndexTop.vue";
  import IndexContent from "../../components/index/IndexContent.vue";
  import ZuoFooter from "../../components/zuonav/ZuoFooter.vue";
  import Login from "../../components/login/Login.vue";
  import PassLogin from "../../components/login/PassLogin.vue";
  import Post from "../../components/login/Post.vue";
  import DownLoad from "../../components/DownLoad/DownLoad.vue";
  import Magnify from "../../components/Magnify/Magnify.vue";
  export default {
    name: 'index',
    data(){
      return{
        isLogin:false,
        isPost:false,
        myact:true,
        isDown:false,
        isPassLogin:false
      }
    },
    components: {
      MyIndex,
      ZuoNav,
      IndexTop,
      IndexContent,
      ZuoFooter,
      Login,
      Post,
      DownLoad,
      Magnify,
      PassLogin
    },
    methods:{
      myLogin:function () {
        this.isLogin = !this.isLogin;
      },
      myPost:function () {
        this.isPost = !this.isPost;
      },
      skipMyPost:function () {
        this.isLogin = false;
        this.isPost = true;
      },
      skipMyLogin:function () {
        this.isLogin = true;
        this.isPost = false;
      },
      closeDown:function () {
        this.isDown = !this.isDown;
      },
      openMyDown:function () {
        this.isDown = !this.isDown;
      },
      skipPassLogin:function () {
        this.isLogin = false;
        this.isPassLogin = true;
      },
      openPost:function () {
        this.isPassLogin = false;
        this.isPost = true;
      }
    }
  }
</script>

<style scoped>
  @import "../../common/style/marx.min.css";
</style>

<template>
  <div class="wrap" >
    <zuo-nav @pass="myLogin" @passPost="myPost" @passDownOpen="openMyDown"></zuo-nav>
    <Login v-show="isLogin" @pass1="myLogin" @pass2="skipMyPost"></Login>
    <Post v-show="isPost" @passPost1="myPost" @passPost2="skipMyLogin"></Post>
    <div class="all">
      <recommend></recommend>
      <more></more>
    </div>
    <zuo-footer></zuo-footer>
    <down-load v-show="isDown" @passDown="closeDown"></down-load>
  </div>
</template>

<script>
  import ZuoNav from '../../components/zuonav/ZuoNav'
  import ZuoFooter from "../../components/zuonav/ZuoFooter.vue"
  import Login from "../../components/login/Login.vue"
  import Post from "../../components/login/Post.vue"
  import More from "../../components/deepness/DeepnessMore.vue"
  import Recommend from "../../components/deepness/DeepnessRecommend.vue"
  import DownLoad from "../../components/DownLoad/DownLoad.vue"
  export default {
    name: 'index',
    data(){
      return{
        isLogin:false,
        isPost:false,
        isDown:false,
      }
    },
    components: {
      ZuoNav,
      ZuoFooter,
      Recommend,
      More,
      Login,
      Post,
      DownLoad
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
      }
    }

  }
</script>

<style scoped>
  @import "../../common/style/marx.min.css";
  .all{
    min-height: 100%;
    width: 100%;
    background-color: #f6f6f6;
  }
</style>

<template>
    <div class="nav">
      <a class="nav_left" href="index.html">
        <span class="logo" >ZUO</span>
        <span class="logo1" >HONEY WASABI</span>
      </a>
      <div class="nav_middle">
        <a href="index.html" :class="{active:isActive}">首页</a>
        <a href="deepness.html" ref="a2" :class="{active:!isActive}">深度</a>
        <a @click="openDown">下载APP</a>
        <div class="zuoSearch">
          <input type="text" placeholder="输入关键字搜索">
          <a href="">
            <img class="search" src="../../assets/zuonav/search.png" alt="">
          </a>
        </div>
      </div>
      <div class="nav_right">
        <div class="zuouser">
          <div>
            <img class="user" src="../../assets/zuonav/user.png" alt="">
          </div>
          <a @click="openLogin">登录</a>
        </div>
        <a @click="openPost">注册</a>
      </div>
    </div>
</template>

<script>
    export default {
      name: 'ZuoNav',
      props: ['isActive'],
      methods:{
        openLogin:function () {
          this.$emit('pass');
        },
        openPost:function () {
          this.$emit('passPost');
        },
        openDown:function () {
          this.$emit('passDownOpen');
        }
      }
    }
</script>

<style scoped>
  .active{
    color: white;
  }
  .nav{
    width: 100%;
    padding-left: 30px;
    padding-right: 30px;
    height: 60px;
    background-color: #262d2f;
    font-size: 14px;
    display: -webkit-flex;
    align-items: center;
    justify-content: space-between;
  }
  a{
    line-height: 20px;
    color: #9ea0a5;
    text-decoration: none;
  }
  .nav_left{
    display: -webkit-flex;
    align-items: center;
  }
  .logo{
    font-size: 20px;
    width: 60px;
    color: white;
    font-style: normal;
  }
  .logo1{
    font-size: 10px;
    color: rgba(255,255,255,.3);
    width: 100px;
  }
  .nav_middle{
    display: flex;
    -ms-flex-align: center;
    align-items: center;
    justify-content: flex-start;
  }
  .nav_middle .zuoSearch{
    display: inline-block;
    position: relative;
  }
  .nav_middle a{
    margin-right: 30px;
    text-decoration: none;
  }
  .nav_middle .zuoSearch .search{
    width: 16px;
  }
  .nav_middle .zuoSearch a{
    display: block;
    width: 20px;
    height: 20px;
    position: absolute;
    right: 6px;
    top: 7px;
    color: #b8b9b9;
    cursor: pointer;
    margin-right: 0;
    text-decoration: none;
  }
  .nav_middle .zuoSearch{
     display: inline-block;
     position: relative;
   }
  .nav_middle a{
    margin-right: 30px;
    text-decoration: none;
  }
  .nav_middle .zuoSearch .search{
    width: 16px;
  }
  .nav_middle .zuoSearch a{
    display: block;
    width: 20px;
    height: 20px;
    position: absolute;
    right: 6px;
    top: 7px;
    color: #b8b9b9;
    cursor: pointer;
    margin-right: 0;
    text-decoration: none;
  }
  .nav_middle input{
    padding: 6px 30px 6px 10px;
    background-color: #464b4d;
    color: #fff;
  }
  .nav_right{
    display: flex;
  }
  .nav_right .zuouser{
    margin-right: 30px;
    display: flex;
  }
  .nav_right .user{
    width: 16px;
  }
</style>

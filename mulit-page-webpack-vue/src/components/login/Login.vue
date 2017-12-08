<template>
  <div>
    <!--蒙版-->
    <div class="zuoLoginWarp" @click="close"></div>

    <div class="zuoLogin">
      <div class="cha" @click="closeLogin">x</div>
      <div class="loginContent">
        <div class="comeback">
          <img src="../../assets/zuologin/logo.png" alt="">
          <span>欢迎回到ZUO</span>
        </div>
        <div class="white">
          <div class="zhanghao">
            <a href="">
              <img class="sina" src="../../assets/zuologin/sina.png" alt="">
              <img class="weChat" src="../../assets/zuologin/wechat.png" alt="">
            </a>
            <p>你可以使用第三方社交账号直接登录</p>
            <div class="or">
              <div class="div1"></div>
              <div class="div2">或者</div>
              <div class="div1"></div>
            </div>
          </div>
          <div>
            <div class="loginText">
              <input class="txt" type="text" placeholder="手机号">
              <div class="yzm">
                <input type="password" placeholder="密码">
              </div>
            </div>
            <div class="forget">
              <div><a @click="skipPost">没有账号？去注册</a></div>
              <div class="pass"><img src="../../assets/zuologin/password.png" alt="">
                <span @click="passlogin">手机密码登录</span>
              </div>
            </div>
          </div>
          <button class="btn" @click="login">登录</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'Login',
        data(){
          return{
            isclick :false
          }
        },
        methods:{
          closeLogin:function () {
            this.$emit('pass1');
          },
          close:function () {
            this.$emit('pass1');
          },
          skipPost(){
            this.$emit('pass2');
          },
          passlogin(){
            this.$emit('openPl')
          },
          login(){
          // axios(options)
            axios({
              method:'post',
              url:'zuoapi/login_by_pass',
              data:{
                phone:'18840801110',
                password:'ymy1993224'
              }
            }).then(function (res) {
              console.log(res.data)
              console.log(res.headers)
              if(res.data.status == 'ok'){
                axios({
                  method:'get',
                  url:'zuoapi/currentuser'
                }).then(function (res) {
                  console.log(res.data)
                })
              }else{
                alert(res.data.error.msg)
              }
            }).catch(function (err) {
              console.log(err)
            })
          }
      }
    }

</script>

<style scoped>
.zuoLoginWarp{
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(39,44,47,.9);
  background-image: linear-gradient(to top,rgba(39,44,47,.9),rgba(39,44,47,.5));
}
.cha{
  position: absolute;
  top: 5px;
  right: -34px;
  font-size: 30px;
  color: #b8b9b9;
  cursor: pointer;
}
.zuoLogin{
    width: 540px;
    position: absolute;
    top: 100px;
    left: 50%;
    margin-left: -270px;
  }
.comeback{
    display: flex;
     -webkit-box-align: center;
     -ms-flex-align: center;
    align-items: center;
     -webkit-box-pack: center;
     -ms-flex-pack: center;
    justify-content: center;
    background-color: #272c2f;
    font-size: 18px;
    padding-top: 25px;
    padding-bottom: 25px;
    color: #fff;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
  }
.comeback img{
  height: 23px;
  padding-right: 15px;
}
.white{
    padding: 30px;
    background-color: #fff;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  }
.zhanghao{
    padding: 0 30px;
    text-align: center;
  }
.zhanghao p{
  margin-top: 13px;
  margin-bottom: 13px;
  font-size: 14px;
  color: #a6a7a7;
}
.zhanghao img{
  margin: 0 20px;
}
input{
  width: 100%;
  background-color: #f7f7f7;
  padding: 14px 20px;
  font-size: 14px;
  line-height: 22px;
  margin-bottom: 20px;
  border: none;
}
.yzm{
  position: relative;
}
.yzm button{
  padding: 12px 20px;
  position: absolute;
  background-color: #1fd7e2;
  right: 0;
  top: 2px;
  border: none;
}
.forget{
  font-size: 14px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 30px;
}
.forget a{
  color:#a6a7a7;
}
.forget img{
  width: 17px;
  padding-right: 3px;
}
.pass{
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.btn{
  font-size: 18px;
  width: 100%;
  background-color: #1fd7e2;
  padding:12px 18px;
}
.or{
  display: flex;
  justify-content: space-between;
  align-items: center ;
  padding: 0 40px;
  margin-bottom: 30px;
}
.or .div1{
   height: 1px;
   width: 138px;
   background-color: #d7d8d8;
}
.or .div2{
   font-size: 14px;
   color: #d7d8d8;
}
</style>

<template>
  <div class="right">
    <div class="right_top">
      <header>热门标签</header>
      <div class="hot_tags">
        <a v-for="(myArrb,index) in arrb" ref="hota" @mouseenter="msHota(index)" @mouseleave="mlHota(index)"
           href="">{{myArrb.inner}}</a>
      </div>
    </div>
    <div class="right_content">
      <header>推荐关注</header>
      <div v-for="(myArr,index) in this.arr" class="userList">
        <div class="user_item">
          <a href="">
            <div class="item_left">
                <p class="p1" ref="user" @mouseenter="msUser(index)" @mouseleave="mlUser(index)">{{myArr.username}}</p>
                <p class="p2" ref="userTxt" @mouseenter="msTxt(index)" @mouseleave="mlTxt(index)">{{myArr.introduction}}</p>
            </div>
            <div class="item_right">
              <img :src= "myArr.avatar" alt="">
              <div class="itemMb"></div>
            </div>
          </a>
        </div>
      </div>
    </div>
    <div class="right_footer">
      <!--右边的小图标-->
      <div class="app_down" ref="appdown" @mouseenter="msDown" @mouseleave="mlDown" @click="opendownload">
        <a>下载ios版 App</a>
        <div class="appimg" >
          <img v-show="isImg1" ref="img1" src="../../assets/zuoindex/graybrid.png" alt="">
          <img v-show="!isImg1" src="../../assets/zuoindex/blackbird.png" alt="">
        </div>
      </div>
      <div class="app_weChat" ref="appwechat" @mouseenter="msWechat" @mouseleave="mlWechat">
        <a href="">关注微信公众号</a>
        <div class="appimg" >
          <img v-show="isImg2" ref="img2" src="../../assets/zuoindex/grayewm.png" alt="">
          <img v-show="!isImg2" src="../../assets/zuoindex/greenewm.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import axios from 'axios'
    export default {
      name: 'indexRight',
      data() {
        return {
          arr: [],
          arrb:[],
          isImg1:true,
          isImg2:true
        }
      },
      mounted() {
        var _this = this;
        axios.get('api/web_reco_users.json',).then(function (res) {
          for (var i in res.data['reco_users']){
            var a = {};
            a.username = res.data['reco_users'][i]['username'];
            a.introduction = res.data['reco_users'][i]['introduction'];
            a.avatar =res.data['reco_users'][i]['avatar'];
            _this.arr.push(a)
          }
        })


        axios.get('api/web_hot_tags.json',).then(function (res1) {
          for (var i in res1.data['hot_tags']){
            var b = {};
            b.inner = res1.data['hot_tags'][i]['content'];
            _this.arrb.push(b)
          }
        })
      },
      methods:{
        msHota:function (index) {
          this.$refs.hota[index].style.color = '#fff';
          this.$refs.hota[index].style.backgroundColor = '#999b9c';
        },
        mlHota:function (index) {
          this.$refs.hota[index].style.color = '#999b9c';
          this.$refs.hota[index].style.backgroundColor = '#eaeced';
        },
        msUser:function (index) {
          this.$refs.user[index].style.color = '#999a9a';
        },
        mlUser:function (index) {
          this.$refs.user[index].style.color = '#535557';
        },
        msTxt:function (index) {
          this.$refs.userTxt[index].style.color = '#535557';
        },
        mlTxt:function (index) {
          this.$refs.userTxt[index].style.color = '#999a9a';
        },

        msDown:function () {
          this.$refs.appdown.style.backgroundColor = 'white';
          this.isImg1 = false;
          console.log()
        },
        mlDown:function () {
          this.$refs.appdown.style.backgroundColor = '#f6f6f6';
          this.isImg1 = true;
        },
        msWechat:function () {
          this.$refs.appwechat.style.backgroundColor = 'white';
          this.isImg2 = false;
        },
        mlWechat:function () {
          this.$refs.appwechat.style.backgroundColor = '#f6f6f6';
          this.isImg2 = true;
        },
        opendownload:function () {
        this.$emit('passdown')
        }
      }
    }
</script>

<style scoped>
  .right{
    width: 223px;
  }
  .right_top{
    width: 100%;
  }
  header{
    font-size: 14px;
    font-weight: 500;
    color: #272c2f;
  }
  .hot_tags{
    margin-top: 18px;
  }
  .hot_tags a{
    display: inline-block;
    margin-right: 10px;
    margin-bottom: 10px;
    padding: 6px 10px;
    font-size: 14px;
    color: #999b9c;
    background-color: #eaeced;
    border-radius: 4px;
    text-decoration: none;
    /*-webkit-transition-duration: .3s;*/
    /*transition-duration: .3s;*/
  }
  .right_content{
    margin-top: 30px;
  }
  .user_item{
    position: relative;
    border-bottom: 1px solid #e4e4e5;
    padding: 10px 0;
    background-color: transparent;
  }
  .user_item a{
    display: flex;
    justify-content: space-between;
    text-decoration: none;
  }
  .item_left{
    width: 140px;
  }
  .item_left .p1{
    font-weight: 500;
    color: #535557;
    font-size: 14px;
    margin: 0;
  }
  .item_left .p2{
    font-size: 12px;
    line-height: 18px;
    color: #999a9a;
    margin: 0;
  }
  .item_right{
    width: 40px;
    height: 40px;
    position: relative;
  }
  .itemMb{
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: black;
    opacity: 0.5;
    display: none;
  }
  .item_right:hover .itemMb{
    display: block;
  }
  .right_footer{
    margin-top: 30px;
  }
  .right_footer a{
    text-decoration: none;
  }
  .app_down,.app_weChat{
    width: 100%;
    height: 50px;
    border: 1px solid #ececec;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-radius: 4px;
  }
  .app_down a,.app_weChat a{
    display: inline-block;
    width: 169px;
    height: 50px;
    border-right: 1px solid #ececec;
    text-align: center;
    line-height: 50px;
    color: #272c2f;
  }
  .app_weChat{
    margin-top: 10px;
  }
  .appimg{
    height: 50px;
    padding: 10px;
  }
</style>

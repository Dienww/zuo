<template>
  <!--点击放大组件-->
  <div class="wrap">
    <div class="magMenban"></div>
    <div class="div1">
      <div class="dix">X</div>
      <div class="magBox">
                <!--左边用户信息，发布内容-->
        <div class="magLeft">
          <!--用户信息-->
          <div class="maglt">
            <div class="magUser">
              <!--用户头像-->
              <div class="whoIssue">
                <img class="magUserImg" src="../../assets/duanwangjijiu/头像.png" alt="">
              </div>
              <!--用户名字-->
              <a href="">{{}}呵呵我就笑笑</a>
              <!--发布时间-->
              <span class="issueTime">发布于九个月前</span>
            </div>
            <div class="magMore">
              <!--分享-->
              <img src="../../assets/zuoindex/share.png" alt="">
              <!--更多-->
              <img src="../../assets/zuoindex/omit.png" alt="">
            </div>
          </div>
          <!--发布内容-->
          <div class="leftContent">
            <!--发布的图片-->
            <img src="../../assets/duanwangjijiu/发表图片.jpeg" alt="" class="magBigImg">
            <!--赞同的圆圈-->
            <!--赞同的圆圈-->
            <!--赞同的圆圈-->
          </div>
        </div>

        <!--右边互动信息-->
        <div class="magRight">
          <div class="magdiv1">
            <div>
              <img src="../../assets/zuoindex/circle.png" alt="">
              <span>赞同这个态度</span>
            </div>
            <span>63个赞同</span>
          </div>
          <div class="magdiv2">
            <span class="arrow"></span>
            <ul class="usermore">
              <li><img src="../../assets/duanwangjijiu/头像.png" alt=""></li>
              <li><img src="../../assets/duanwangjijiu/头像.png" alt=""></li>
              <li><img src="../../assets/duanwangjijiu/头像.png" alt=""></li>
              <li><img src="../../assets/duanwangjijiu/头像.png" alt=""></li>
              <li><img class="omit" src="../../assets/zuoindex/omit.png" alt=""></li>
            </ul>
          </div>
          <div class="magdiv3">
            <div class="div3top">这个异形穹顶是用热压木板「编织」出来的。再一看，都是伊姆斯的椅子么？原来这是herman miller在新加坡的旗舰店。</div>
            <div class="div3tag">
              <a href="">
                <span></span>
                <span>{{}}空间</span>
              </a>
              <a href="">
                <span></span>
                <span>{{}}零售空间</span>
              </a>
              <a href="">
                <span></span>
                <span>{{}}Herman Miller</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
    export default {
        name: 'Magnify'
    }
</script>

<style scoped>
  .wrap{
    display: none;
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }
  .magMenban{
    width: 100%;
    height: 100%;
    background-color: rgba(39,44,47,.9);
  }
  .div1{
    position: absolute;
    top: 30px;
    width: 100%;
    min-height: 600px;
  }
  .magBox {
    width: 850px;
    margin: 0 auto;
    border-radius: 4px;
    position: relative;
    background-color: #fff;
    display:flex;
    justify-content: space-between;

  }
  /*叉*/
  .dix{
    font-size: 20px;
    color: #b8b9b9;
    cursor: pointer;
    position: absolute;
    top: 10px;
    right: -60px;
  }
  .magLeft{
    width: 540px;
    padding-top: 5px;
    padding-left: 18px;
    padding-bottom: 15px;
    box-sizing: border-box;
  }
  .magLeft .maglt{
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 14px;
  }
  .magLeft .maglt .magUser{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 0
  }
   .whoIssue{
    width: 40px;
    height: 40px;
    border-radius: 50%;
    overflow:hidden;
  }
  .magLeft .maglt .magUser a{
    padding: 0 10px;
    color: black;
    text-decoration: none;
  }
  .magLeft .maglt .magUser .issueTime{
    color: #a6a7a7;
  }
  .magLeft .maglt .magMore img{
    width: 17px;
    height: 17px;
    margin-left: 18px;
  }

  .leftContent img{
    width: 540px;
    height: 540px;
    border-radius: 5px;
  }
  .magRight{
    width: 280px;
  }
  .magRight .magdiv1{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 19px 25px 18px;
    color: #a6a7a7;
    font-size: 14px;
  }
  .magRight .magdiv1 div{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .magRight .magdiv1 div img{
    width: 20px;
    height: 20px;
  }
  .magRight .magdiv2 ul{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-left: 0;
  }

  .magRight .magdiv2{
    padding: 10px;
    background-color: #eaeced;
    border-radius: 4px;
    height: 60px;
    margin-left: 15px;
    margin-right: 15px;
  }
  .magRight .magdiv2 ul li{
    list-style: none;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    overflow: hidden;
  }
  .magRight .magdiv3{
    padding-left: 15px;
    padding-top: 15px;
    padding-right: 15px;
  }
  .magRight .magdiv3 .div3top{
    padding: 13px 0;
    border-top: 1px solid #ececec;
    word-wrap: break-word;
    color: #595c5d;
    font-size: 15px;
  }
  .magRight .magdiv3 .div3tag{
    padding-bottom: 13px;
    flex-wrap: wrap;
  }
  .magRight .magdiv3 .div3tag a{
    padding-right: 15px;
    color: #a6a7a7;
    display: flex;
    align-items: center;
    margin-top: 5px;
    margin-bottom: 5px;
    text-decoration: none;
  }
</style>

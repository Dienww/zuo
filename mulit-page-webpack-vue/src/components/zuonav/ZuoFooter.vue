<template>
  <div class="footer">
      <div class="fw">
        <div class="ftt">
          <a href="">关注公众号</a>
          <a href="">关于<strong>ZUO</strong></a>
          <a href="">反馈吐槽</a>
        </div>
        <div class="ftb">
          <span>上海设慧网络科技有限公司2016版权所有</span>
          <span>沪ICP备15013372号</span>
        </div>
      </div>
  </div>
</template>

<script>
    export default {
        name: 'ZuoFooter'
    }
</script>

<style scoped>
 .footer{
   background-color: #eaeaea;
 }
  .fw{
    max-width: 420px;
    margin: 0 auto;
    padding-top: 18px;
    padding-bottom: 18px;
    text-align: center;
  }
 .ftt{
   width: 100%;
   display: flex;
   justify-content: space-around;
 }
 .ftt a{
   text-decoration: none;
   font-size: 13px;
   color: #999a9a;
   margin-bottom: 10px;
 }
  .ftb{
    font-size: 13px;
    color: #b8b9b9;
    display: flex;
    justify-content: space-between;
  }

</style>

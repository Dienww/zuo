<template>
  <div class="zuoWelcome">
    <div class="zwBox">
      <h1>{{title}}</h1>
      <div class="subtip">
        <span>{{world}}<br>{{worlds}}</span>
      </div>
      <button @click="create">创建ZUO账号</button>
      <img class="fork" src="../../assets/zuoindex/Fork.png" alt="">
    </div>
  </div>
</template>

<script>
    export default {
        name: 'IndexTop',
        data(){
          return{
            title:'可能是全宇宙最ZUO的图片社区',
            world:'和像你一样认真对待生活的人一起',
            worlds : '从设计的视角，重新认识世界'
          }
        },
        methods:{
          create:function () {
            this.$emit('pass-c-post')
          }
        }
    }

</script>

<style scoped>
  .zuoWelcome{
    position: relative;
    background-image: url(../../assets/zuoindex/overlay.png);
    background-repeat: repeat;
    background-color: #eaeced;
  }
  .zuoWelcome .zwBox{
    width: 790px;
    margin: 0 auto;
    text-align: center;
    padding-top: 30px;
    padding-bottom: 30px;
  }
  .zuoWelcome .zwBox h1{
    font-size: 24px;
    margin: 0;
    font-weight: 700;
    color: #272c2f;
    border: none;
  }
  .zuoWelcome .zwBox .subtip{
    margin-top: 15px;
    margin-bottom: 18px;
    font-size: 16px;
    color: #5d6c75;
  }
  .zuoWelcome .zwBox button{
    width: 200px;
    font-size: 16px;
    background-color: #1fd7e2;
    color: #fff;
  }
  .fork{
    width: 20px;
    position: absolute;
    top: 35px;
    right: 30px;
  }
</style>

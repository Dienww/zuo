<template>
<div class="wrapDown">
  <div class="downMb" @click="closeD"></div>
  <img src="../../assets/zuodown/download.png" alt="">
</div>
</template>

<script>
    export default {
        name: 'DownLoad',
        methods:{
            closeD:function () {
              this.$emit('passDown')
            }
        }
    }
</script>

<style scoped>
  .wrapDown{
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }
  .downMb{
    width:100%;
    height:100%;
    background-color: rgba(0,0,0,0.8);
  }
  img{
    position: absolute;
    top: 50%;
    left: 50%;
    width: 436px;
    height: 440px;
    margin-top: -220px;
    margin-left: -218px;
  }
</style>

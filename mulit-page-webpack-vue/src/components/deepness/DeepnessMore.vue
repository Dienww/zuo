<template>
    <div class="moreBox">
      <div class="moreTitle">
        <p>更多文章</p>
      </div>
      <div class="moreContent">
        <div class="moreItem" v-for="aa in this.moreArr">
          <a href="">
          <div class="top" :style="{backgroundImage: 'url('+ aa.banner +')'}"></div>
          </a>
          <div class="bottom">
            <a href="" class="smallTitle">{{aa.title}}</a>
            <div class="smallTitle1">
              <span class="author">ZUO先生</span>
              <span class="time">{{aa.timeAgo}}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
  import axios from 'axios'
  export default {
      name: 'More',
    data(){
      return{
        moreArr:[],
      }
    },
    mounted() {
      var _this = this;
      axios.get('api/articles.json').then
//      axios.get('api/articles').then
      (function (res) {
        _this.moreArr = res.data.articles;
      })
    }
  }
</script>

<style scoped>
  .moreBox{
    width: 930px;
    margin: 0 auto;
  }
  .moreContent{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
  }
  .moreTitle{
    font-size: 20px;
    font-weight: 700;
    text-align: center;
    padding-top: 30px;
    padding-bottom: 30px;
  }
  .myContent img{
    width: 100%;
    height: 100%;
    border-radius: 4px;
    overflow: hidden;
  }
  .moreItem{
    display: block;
    width: 219px;
    margin-bottom: 18px;
  }
  .moreItem a{
    text-decoration: none;
  }
  .top{
    width: 100%;
    height: 162px;
    background-size: cover;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
  }
  .bottom{
    padding: 15px;
    background-color: #fff;
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
  }
  .smallTitle{
    height: 105px;
    font-size: 14px;
    color: #272c2f;
    line-height: 20px;
    display: block;
  }
  .smallTitle1{
    display: flex;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    font-size: 12px;
    color: #272c2f;
  }
  .time{
    color: #a6a7a7;
  }
</style>

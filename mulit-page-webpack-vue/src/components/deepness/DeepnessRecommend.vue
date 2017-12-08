<template>
      <div class="readBox">
        <div class="readTitle">
          <p>推荐阅读</p>
        </div>
        <div class="readContent">
          <div class="myContent" v-for="topArr in this.recommendArr">
            <!--背景图-->
            <img :src="topArr.banner" alt="">
            <!--蒙版-->
            <div class="menban">
              <div class="fontBox">
                <div class="top">{{topArr.title}}</div>
                <div class="zhongjian">{{topArr.summary}}</div>
                <div class="footer">
                  <div class="tags">
                    <span></span>
                    <span>{{topArr.sceneTagName}}</span>
                  </div>
                  <div class="time">
                    <span>{{topArr.timeAgo}}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
</template>

<script>
  import axios from 'axios'
    export default {
      name: 'Recommend',
      data(){
        return{
          recommendArr:[],
        }
      },
      mounted() {
        var _this = this;
//        axios.get('api/hot_articles.').then
        axios.get('api/hot_articles.json').then
        (function (res) {
          _this.recommendArr = res.data.hot_articles;
          console.log(_this.recommendArr)
        })
      }
    }
</script>

<style scoped>
  .readBox{
    width: 930px;
    margin: 0 auto;
  }
  .readContent{
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .readTitle{
    font-size: 20px;
    font-weight: 700;
    text-align: center;
    padding-top: 30px;
    padding-bottom: 30px;
  }
  .myContent{
    width: 298px;
    height: 452px;
    position: relative;
    box-sizing: border-box;
  }
  .myContent img{
    width: 100%;
    height: 100%;
    border-radius: 4px;
    overflow: hidden;
  }
  .menban{
    background-color: rgba(0,0,0,.2);
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    bottom: 0;
  }
  .myContent:hover .menban{
    background-color: rgba(0,0,0,.5);
    transition: 0.5s;
  }
  .fontBox{
    width: 100%;
    position: absolute;
    bottom: 0;
    color: white;
    padding: 18px;
  }
  .fontBox .top{
    font-size: 18px;
    font-weight: 700;
    line-height: 24px;
    margin-bottom: 10px;
    height: auto;
  }
  .fontBox .zhongjian{
    font-size: 14px;
    font-weight: 400;
    color: rgba(255,255,255,.8);
    padding-top: 10px;
    margin-bottom: 23px;
  }
  .fontBox .footer{
    display: flex;
    font-size: 14px;
    font-weight: 400;
    -ms-flex-align: center;
    align-items: center;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    border-top: 1px solid rgba(255,255,255,.2);
    padding:15px 0 0 0;
  }
</style>

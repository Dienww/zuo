<template>
  <!--话题-->
  <div class="topic" ref="topicTop" @mouseenter="meTopic" @mouseleave="mlTopic">
    <!--重新认识文具部分-->
    <div class="topicTop"  :style="{backgroundImage:'url('+cover+')'}">
      <div class="menban">
        <div class="div1">
          <p class="topic_title">话题</p>
          <div class="yellowLine"></div>
        </div>
        <div class="div2">
          <span>{{topic['title']}}</span><img src="../../assets/zuoindex/arrow.png" alt="">
        </div>
        <div class="div3">
          <span>{{topic['collect_count']}}人收藏</span>
          <span>|</span>
          <span>{{topic['comment_count']}}个讨论</span>
        </div>
      </div>
    </div>
    <!--留言讨论-->
    <div class="carousel">
      <!--轮播-->
      <a class="CarouselLink" href="">{{Authors[num]}}：</a>
      <span class="CarouselContent" v-html="Comments[num]">
            {{Comments[num]}}
      </span>
    </div>
  </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: 'topic',
      data() {
        return {
          topic: [],
          TopicBg: '',
          Comments: [],
          Authors: [],
          num:'',
          cover:''
        }
      },
      mounted() {
        var _this = this;
//        axios.get('api/topics',).then(function (response) {
       axios.get('api/topics.json',).then(function (response) {
          _this.cover = response.data.topic.cover;
          _this.topic = response.data.topic;
          _this.TopicBg = response.data.topic.cover;
          for (var i in response.data.topic.comments) {
            _this.Comments.push(response.data.topic.comments[i].text);
            _this.Authors.push(response.data.topic.comments[i].author.username);
          }
        });
        setInterval(getIntervalNum,5000);
        function  getIntervalNum() {
          var a='';
          a=Math.floor(Math.random()*5);
          _this.num=a;
        }
        getIntervalNum();
     },

      methods:{
          meTopic:function () {
            this.$refs.topicTop.style.boxShadow =  '3px 3px 10px #eee';
          },
         mlTopic:function () {
           this.$refs.topicTop.style.boxShadow = '0 0 0 '
         }
      }

    }

</script>

<style scoped>
  /*话题讨论版块*/
  .topic{
    width: 100%;
    margin-bottom: 30px;
    border-radius: 4px;
    cursor: pointer;
    color: white;
    overflow: hidden;
  }
  /*话题*/
  .topicTop{
    width: 100%;
    height: 167px;
    position: relative;
    /*background-image: url(http://ac-llsfhjiu.clouddn.com/d1186aaea44af125e918.png?imageView/1/w/540/h/540/q/100/format/jpeg);*/
  }
  .topic .div1{
    font-size: 14px;
  }
  .topic .div1 p{
    margin-bottom: 10px;
  }
  .topic .div1 .yellowLine{
    width: 20px;
    height: 5px;
    border-radius: 6px;
    background-color: #F8D440;
  }
  .topic .div2{
    font-size: 22px;
    line-height: 28px;
    margin-top: 30px;
    margin-bottom: 18px;
    display: flex;
    flex-direction:row;
    align-items: center;

  }
  .topic .div2 img{
    width: 24px;
    height: 24px;
  }
  .topic .div3{
    align-items: center;
    color: rgba(255,255,255,.6);
    font-size: 14px;
  }
  .topic .carousel{
    width: 100%;
    padding: 18px 20px;
    font-size: 13px;
    line-height: 22px;
    height: 80px;
    color: black;
    background-color: white;
  }
  .carousel .span2{
    color: #999a9a;
    height: 40px;
    overflow: hidden;
  }
  .menban{
    position: absolute;
    padding: 18px 30px;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0,0,0,.4);
  }
</style>

<template>
  <transition name="slide">
    <div class="chatroom">
      <div class="back">
        <router-link to='/chat' >
          <img class="img" src="../../assets/返回.png" @click='clearContent' height="16" width="19" />
        </router-link>
        <span class="logo" @click="gotoUser ()">
          <img src="../../assets/我.png" height="28" width="28">
        </span>
      </div>
      <div class="content">
        <div class="content-wrapper" ref="wrapper">
          <div class="content-text">
            <div class="content-top">
              <p>~~~现在可以和我聊天了~~~</p>
            </div>
            <div class="content-body" ref="body">
              <ul class="inHtml" v-for="item in content" :key="item.id">
                <li class="ask"  v-show="item.askContent">
                  <img :src="item.askImg" />
                  <p>{{item.askContent}}</p>
                </li>
                <li class="reply" v-show="item.replyContent">
                  <img :src="item.replyImg" />
                  <p>{{item.replyContent}}</p>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="bottom">
        <div class="send">
          <input
            type="text"
            placeholder="请输入聊天内容"
            class="sText"
            ref="sTest"
          />
          <input type="button" class="btn" value="发送" @click="sendContent" />
        </div>
      </div>
      <router-view></router-view>
    </div>
  </transition>
</template>
<script>
export default {
  data () {
    return {
      show: 0,
      text: '',
      randomReply: [
        '你谁啊？',
        '请你再说一遍！',
        '想和我聊天？得先夸我！',
        '我不知道你在讲什么。。。',
        '不好意思，我不想和你说话。',
        '先告诉我你是谁。',
        '竖子不足以谋也！',
        '我选择沉默',
        '来吧，一起吹牛逼。。',
        '我很困，不想聊天',
        '别废话，先给我讲个笑话',
        '你从哪里来',
        '心情不好，最好别搭理我',
        '等我忙完再回复你',
        '敢问尊姓大名',
        '近来可好？',
        '看来你是想和我聊天',
        '你是要请我吃饭吗？',
        '先给我一个让我回复你的理由',
        '哈哈哈'
      ],
      content: [
        // {
        //   id: '001',
        //   replyImg: 'https://images.pexels.com/photos/2997721/pexels-photo-2997721.jpeg?auto=compress&cs=tinysrgb&dpr=3&h=750&w=1260',
        //   askImg: 'https://images.pexels.com/photos/2545049/pexels-photo-2545049.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500',
        //   askContent: '你好啊',
        //   replyContent: '谢谢'
        // }
      ]
    }
  },
  methods: {
    clearContent () {
      this.content = []
    },
    gotoUser () {
      console.log(123)
    },
    sendContent () {
      this.text = this.$refs.sTest.value
      if (this.text !== '') {
        this.content.push({
          askImg: 'https://images.pexels.com/photos/1694649/pexels-photo-1694649.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940',
          askContent: this.text
        })

        setTimeout(() => {
          this.content.push({
            replyImg: 'https://images.pexels.com/photos/2986524/pexels-photo-2986524.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500',
            replyContent: this.randomReply[Math.floor(Math.random() * 19)]
          })
        }, 1000)
      }
      this.$refs.sTest.value = '' // 清空输入框的内容
    }
  }
}
</script>

<style scoped>
  .chatroom{
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 19;
    background-color: #f0fbf6;
  }
  .back{
    background: #26a2ff;
    height: 50px;
    color: #fff;
    position: fixed;
    width: 100%;
  }
  .back .img{
    position: absolute;
    top: 25px;
    margin-top: -8px;
    left: 14px;
  }
  .back .dissname{
    position: absolute;
    font-size: 20px;
    top: 25px;
    margin-top: -10px;
    left: 50px;
    padding-left: 10px;
    border-left: 1px solid #000;
  }
  .back .logo{
    position: absolute;
    font-size: 20px;
    top: 30px;
    margin-top: -15px;
    right: 20px;
  }
  .content{
    position: fixed;
    top: 50px;
    bottom: 50px;
    left: 0;
    right: 0;
  }
  .content-wrapper{
    height: 100%;
    overflow: hidden;
  }
  .content-top{
    font-size: 14px;
    color: rgba(153,153,153,0.6);
    text-align: center;
    margin-top: 15px;
  }
  .content-body{
    position: relative;
    padding: 20px 10px;
  }
  .content-body li {
    position: relative;
    overflow: hidden;
    margin-bottom: 15px;
    line-height: 28px;
  }
  .inHtml img {
    position: relative;
    width: 40px;
    height: 40px;
  }
  .ask {
    text-align: right;
  }
  .reply {
    text-align: left;
  }
  .ask img {
    float: right;
    margin-left: 15px;
  }
  .reply img {
    float: left;
    margin-right: 15px;
  }
  .reply p, .ask p {
      margin-top: 2px;
    border-radius: 4px;
    text-align: left;
    font: 14px 'Microsoft YaHei';
    line-height: 30px;
  }
  .ask p {
    float: right;
    padding: 3px 10px;
    max-width: 182px;
    background: #26a2ff;
    color: #fff;
  }
  .reply p {
    left: 2pc;
    float: left;
    padding: 3px 10px;
    max-width: 190px;
    background: #fff;
  }
  .bottom{
    position: fixed;
    height: 50px;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: #fff;
  }
  .send{
    display: flex;
  }
  .sText{
    flex: 6;
    height: 30px;
    margin: 10px;
    border: 0;
    padding-left: 8px;
    border-bottom: 1px solid#26a2ff;
    font-size: 15px;
  }
  .sText.active{
    background-color: red;
  }
  .btn{
    flex: 1;
    width: 65px;
    height: 30px;
    margin: 10px 10px;
    border: 0;
    border-radius: 5px;
    text-align: center;
    font-size: 16px;
    color: white;
    background-color: #26a2ff;
  }

  .slide-enter-active,.slide-leave-active{
    transition: all 0.3s;
  }
  .slide-enter,.slide-leave-to{
    transform: translate3d(100%, 0, 0);
  }
</style>

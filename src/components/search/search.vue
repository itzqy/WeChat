<template>
  <transition name="slide">
    <div class="search">
      <div class="back">
        <img class="back-img" src="../../assets/返回.png"  @click="back" height="16" width="19" />
        <div class="serch-box">
          <input
            type="text"
            placeholder="请输入搜索内容"
            v-model="inputText"
            class="sText"
            ref="sText"
          />
          <img class="logo" src="../../assets/搜索.png" height="20" width="20" @click="gogogo" />
        </div>
      </div>
      <div class="content">
        <div class="content-text">
          <h2 ref="tips">搜索指定内容</h2>
          <div class="kind">
            <span>朋友圈</span>
            <span>文章</span>
            <span>公众号</span>
          </div>
          <div class="kind">
            <span>小说</span>
            <span>音乐</span>
            <span>表情</span>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  data () {
    return {
      inputText: ''
    }
  },
  methods: {
    back () {
      this.$router.back()
    },
    gogogo () {
      window.open('https://www.baidu.com/s?wd=' + this.inputText)
      this.inputText = ''
    }
  },
  computed: {
  }
}
</script>

<style scoped>
  *{
    transition: all 0.5s;
  }
  .search{
    position: fixed;
    top: 0px;
    bottom: 0px;
    left: 0;
    right: 0;
    background-color: #f0fbf6;
    z-index: 99;
  }
  .back{
    background: #26a2ff;
    height: 50px;
    color: #fff;
    position: fixed;
    width: 100%;
  }
  .back-img{
    position: absolute;
    top: 25px;
    margin-top: -8px;
    left: 14px;
  }
  .back span{
    position: absolute;
    font-size: 20px;
    top: 25px;
    margin-top: -10px;
    left: 50px;
    padding-left: 10px;
    border-left: 1px solid #000;
    color: #fff;
  }
  .serch-box{
    display: flex;
    position: absolute;
    width: 90%;
    height: 100%;
    right: 0;
  }
  .sText{
    position: absolute;
    right: 50px;
    height: 30px;
    width: 70%;
    top: 10px;
    border: 0;
    padding-left: 28px;
    background-color: #fff;
    font-size: 14px;
    color: #fff;
  }
  .result{
    position: fixed;
    padding: 6px 20px 10px 20px;
    top: 50px;
    left: 60px;
    width: 60%;
    background-color: #ebebeb;
    color: #1e2b39;
    border: 1px solid #09BB07;
  }
  .result li{
    margin: 8px auto;
    font-size: 16px;
  }
  .logo{
    position: absolute;
    top: 15px;
    right: 20px;
  }
  .content{
    position: fixed;
    top: 50px;
    left: 0;
    right: 0;
    bottom: 0;
  }
  .content h2{
    font-size: 14px;
    text-align: center;
    margin-top: 60px;
    color: rgba(153,153,153,1);
  }

  .kind{
    display: flex;
    justify-content: center;
    padding: 0 40px;
  }
  .kind span{
    flex: 1;
    display: flex;
    margin-top: 40px;
    color: #26a2ff;
    justify-content: center;
  }

  .slide-enter-active,.slide-leave-active{
    transition: all 0.5s;
    opacity: 1;
  }
  .slide-enter,.slide-leave-to{
    transform: scale(0.1,0.1);
    opacity: 0;
  }
</style>

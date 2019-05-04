<template>
  <div id="app">
    <div>
      <ul class="left" @click.stop.prevent='go'>
        <li class="yu" data-name='/'>{{$t("app.yu")}}</li>
        <li data-name='/jianzhi'>{{$t("app.part")}}</li>
        <li>{{$t("app.recruitment")}}</li>
      </ul>
      <ul class="right">
        <li>{{$t("app.login")}}</li>
        <li>{{$t("app.registered")}}</li>
        <li>
          <select v-model='lang' @change='langChange'>
            <option value="zhCHS">简体中文</option>
            <option value="en">English</option>
            <option value="zhCHT">繁體中文</option>
          </select>
        </li>
      </ul>
    </div>
  <!-- 组件引用 -->
    <router-view/>

    <div class="foot">
      <div>
        <h3>新手指南</h3>
        <div>
          <span>注册新用户</span>
          <span>雇主入门</span>
        </div>
        <div>
          <span>技术兼职入门</span>
          <span>规则中心</span>
        </div>
      </div>
      <div>
        <h3>我是雇主</h3>
        <div>
          <span>发布招聘需求</span>
          <span>挑选技术兼职</span>
        </div>
      </div>
      <div>
        <h3>我是技术兼职</h3>
        <div>
          <span>发布简历</span>
          <span>投递职位</span>
        </div>
      </div>
      <div>
        <h3>交易保障</h3>
        <div>
          <span>乐鱼担保交易</span>
          <span>雇主保障</span>
        </div>
        <div>
          <span>众包平台</span>
        </div>
      </div>
    </div>
    <div class="footer">
      <div>
        <ul>
          <li>关于我们</li>
          <li>企业文化</li>
          <li>联系方式</li>
          <li>使用协议</li>
          <li>网站地图</li>
          <li>友情链接</li>
          <li>网站留言</li>
        </ul>
      </div>
      <div>
        ©2016 乐鱼网 All Rights Reserved 鲁ICP备15008460号
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      lang:'zhCHS'
    }
  },
  methods: {
    go(ev){
     this.$router.push(ev.target.dataset.name)
    },
    langChange(){
      this.$i18n.locale = this.lang
      console.log(this.lang)
    }
  },
}
</script>

<style>
*{
  margin: 0 auto;
  box-sizing: border-box;
}
#app {
  text-align: center;
  color: #808080;
}
#app>div:nth-child(1){
  width: 100%;
  height: 40px;
  line-height: 40px;
  background:#f8f8f8;
}
ul{
  list-style: none;
  display: inline-block;
}
ul>li{
  float: left;
  padding: 0 20px;
  color: #808080; 
}
.yu{
  font-size:20px;
}
.left{
  float: left;
}
.left>li{
  border-right: 1px solid white;
}
.right{
  float: right;
  margin-right:0px;
  font-size: 13px;
}
body{
  min-width: 1000px;
}
.foot{
  width: 100%;
  height: 180px;
  background: #606873;
  color: white;
  padding: 0 150px;
}
.foot>div{
  float: left;
  width: 25%;
  margin-top: 50px;
}
.foot>div>div{
  float: left;
  font-size: 14px;
  width: 200px;
  padding-top: 20px;
  margin-left:50px;
}
.foot>div>div>span{
  width: 50%;
  float: left;
}
.footer{
  font-size: 14px;
  margin-top: 20px;
}
</style>

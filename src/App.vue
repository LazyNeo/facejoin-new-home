 <template>
  <div id="app">
    <div class="header"
         :class="{'header-active': scrollEvt.isHeader}">
      <div class="header-wrap">
        <h1 class="header-title">
          <a href="javascript:void(0);">斑马活动管家</a>
        </h1>
        <ul class="header-nav">
          <li class="header-nav-item">首页</li>
          <li class="header-nav-item">
            <a href="home.html#upLoadActivity">上传活动</a>
          </li>
          <li class="header-nav-item">
            <a href="home.html#manageActivity">活动管理</a>
          </li>
        </ul>
        <ul class="header-nav login-nav">
          <li class="header-nav-item">
            <a href="home.html#signUp">注册</a>
          </li>
          <li class="header-nav-item">
            <a href="home.html#login">登录</a>
          </li>
        </ul>
      </div>
    </div>
    <home :is-public="scrollEvt.isPublic",
          :is-data="scrollEvt.isData",
          :is-cnt="scrollEvt.isCnt"></home>
    <div class="footer">
      <div class="footer-wrap ui-clearfix">
        <div class="footer-title ui-ft-l"><img src="./assets/logo.png">斑马活动管家</div>
        <div class="footer-right ui-ft-r">
          <div class="footer-link">
            <a href="home.html#aboutUs" target="_blank" class="footer-link">关于我们</a>
            <a href="home.html#adCo" target="_blank">广告合作</a>
            <a href="home.html#contactUs" target="_blank">联系我们</a>
            <a href="home.html#joinUs" target="_blank">招聘英才</a>
          </div>
          <div>Copyright © 2016-2021 FaceJoin. All Rights Reserved. 粤ICP备16029009号</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import home from './components/Home'

export default {
  data () {
    return {
      scrollEvt: {
        isHeader: false,
        isPublic: false,
        isData: false,
        isCnt: false
      }
    }
  },
  components: {
    home
  },
  ready () {
    window.onscroll = (e) => {
      const scrollTop = window.pageYOffset
      if (scrollTop >= 5) {
        this.scrollEvt.isHeader = true
        if (scrollTop >= 280) {
          this.scrollEvt.isPublic = true
          if (scrollTop >= 780) {
            this.scrollEvt.isData = true
            if (scrollTop >= 1280) {
              this.scrollEvt.isCnt = true
            }
          }
        }
      } else {
        this.scrollEvt.isHeader = false
      }
    }
  }
}
</script>

<style lang="less">
@import './assets/css/index.less';

body {
  .re-body;
  min-width: 980px;
  font: 14px/1.6 Helvetica Neue,Helvetica,PingFang SC,Arial,Microsoft Yahei,sans-serif;
}
a{
  text-decoration: none;
}
.header {
  position: fixed;
  z-index: 1;
  width: 100%;
  padding-top: 14px;
  transition: all .3s ease;
}
.header-wrap {
  .ui-wrap-1080;
}
.header-title {
  .re-h;
  display: inline-block;
  a {
    .re-a;
    display: block;
    font-size: @fs-18;
    transition: color .3s;
    color: #fff;
  }
}
.header-nav {
  .re-list-fib;
  display: inline-block;
  padding: 0 0 0 50px;
  li a{
    color: rgba(255, 255, 255, 0.7);
  }
}
.login-nav{
  float: right;
  li{
    padding: 0 20px;
    a{
      color: rgba(255, 255, 255, 0.7);
    }
  }
}
.footer-link a{
  color: #666;
}
.header-nav-item {
  .ui-nav-text;
  display: inline-block;
  padding: 0 40px;
  letter-spacing: 1px;
  cursor: pointer;
  transition: all .3s;
  &:hover {
    color: #fff;
  }
}
.header-active {
  background: #fff;
  padding-top: 0;
  box-shadow: 0 2px 15px rgba(0, 0, 0, .1);
  .header-title a {
    color: #333;
  }
  .header-nav-item {
    color: #979aa2;
    &:hover {
    color: #333;
    }
  }
}
.footer {
  font-size: @fs-16;
  line-height: 30px;
  color: #666;
  background: #f8f8f8;
}
.footer-wrap {
  .ui-wrap-1080;
  padding: 70px 0 40px;
}
.footer-title {
  font-size: @fs-20;
  line-height: 80px;
  color: #333;
  cursor: pointer;
  img {
    height: 25px;
    margin: 0 8px;
    vertical-align: text-bottom;
  }
}
.footer-right {
  line-height: 40px;
  text-align: right;
  a {
    margin-left: 20px;
    letter-spacing: 1px;
    cursor: pointer;
    &:hover {
      color: #333;
    }
  }
}
</style>

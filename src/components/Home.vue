<template>
	<div class="home">
    <div class="home-banner">
      <div class="home-banner-img"></div>
    </div>
    <div class="home-body">
      <div class="home-title">
        <h2>「活」色生香</h2>
        <h3>活动如此简单</h3>
      </div>
      <div class="home-section">
        <div class="section-text ui-ft-l"
             :class="{'section-text-active': isPublic}">
          <h2 class="section-title">发布活动</h2>
          <p class="section-desc">轻松发布活动，快速生成线上活动手机展示页</p>
          <p class="section-desc">二维码快速报名，后台高效管理报名用户</p>
          <p class="section-desc">一键群发短信通知</p>
        </div>
        <div class="section-show ui-ft-r ui-of-h"
             :class="{'show-public-active': isPublic}">
          <!-- <img class="section-public" src="../assets/public.gif"> -->
          <div class="show-scene">
            <div class="scene-bg"></div>
            <div class="scene-pc">
              <div class="pc-outer"></div>
              <div class="pc-inner"></div>
              <div class="pad-outer"></div>
              <div class="pad-inner"></div>
            </div>
            <div class="scene-msg">
              <div class="msg1">
                <div class="msg1-content"></div>
              </div>
              <div class="msg2">
                <div class="msg2-content"></div>
              </div>
              <div class="msg3"></div>
              <div class="msg3-content"></div>
            </div>
          </div>
          <div class="show-masker"></div>
          <div class="show-phone">
            <div class="phone-outer"></div>
            <div class="phone-inner">
              <div class="phone-mail">
                <div class="phone-letter"></div>
                <div class="phone-enve"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="home-section section-data">
        <div class="section-show ui-ft-l ui-of-h"
             :class="{'show-data-active': isData}">
          <div class="histogram-x"></div>
          <div class="histogram-x-arrow">&#xe608;</div>
          <div class="histogram-y"></div>
          <div class="section-histogram">
            <span class="histogram-item"></span>
            <span class="histogram-item"></span>
            <span class="histogram-item"></span>
            <span class="histogram-item"></span>
            <span class="histogram-item"></span>
          </div>
          <div class="section-pie">
            <div class="pie-glass">&#xe60c;</div>
            <div class="pie-out">
              <div class="pie-circle1">
                <div class="pie-circle1-left"></div>
                <div class="pie-circle1-right"></div>
              </div>
              <div class="pie-circle2"></div>
              <div class="pie-circle3">
                <span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span><span></span>
              </div>
              <div class="pie-circle4"></div>
              <div class="pie-circle5"></div>
              <div class="pie-circle6"></div>
              <span class="pie-data">30.13%</span>
              <span class="pie-data">15.78%</span>
              <span class="pie-data">66.89%</span>
              <span class="pie-data">83.45%</span>
            </div>
          </div>
        </div>
        <div class="section-text ui-ft-r"
             :class="{'section-text-active': isData}">
          <h2 class="section-title">数据分析</h2>
          <p class="section-desc">运用数据挖掘技术多维度全方位分析参与用户数据</p>
          <p class="section-desc">根据数据分析结果指导活动推广</p>
          <p class="section-desc">提高组织方活动举办效率</p>
        </div>
      </div>
      <div class="home-section">
        <div class="section-text ui-ft-l"
             :class="{'section-text-active': isCnt}">
          <h2 class="section-title">资源对接</h2>
          <p class="section-desc">平台接入海量品牌赞助商以及物料资源</p>
          <p class="section-desc">为组织活动提供优质商业资源</p>
        </div>
        <div class="section-show ui-ft-r"
             :class="{'show-cnt-active': isCnt}">
          <div class="section-cloud1">&#xe6ec;</div>
          <div class="section-cloud2">&#xe6ec;</div>
          <div class="section-balloon">
            <div class="balloon-top">
              <div class="balloon-inner"></div>
            </div>
            <div class="balloon-box"></div>
          </div>
          <div class="section-cloud3">&#xe764;</div>
          <div class="section-cloud4">&#xe764;</div>
        </div>
      </div>
      <div class="home-hot">
        <h2 class="hot-title">热门活动</h2>
        <p class="hot-desc"><span>不止于眼前，生活在别处</span></p>
        <div class="hot-item"
             v-for="item of hotActv">
          <div class="hot-actv"
               :class="{'hot-actv-active': item.isOpen}"
               :style="{backgroundImage: 'url(' + item.post + ')'}"
               @click="openActv($index)">
            <div class="hot-actv-masker"></div>
            <div class="hot-actv-wrap">
              <div class="actv-read">
                <p class="actv-num">{{item.readNum}}</p>
                <p class="actv-name">阅读数</p>
              </div>
              <div class="actv-content">
                <h3 class="actv-title">{{item.title}}</h3>
                <p class="actv-info">
                  <span>主办方： {{item.hoster}}</span>
                  <span>时间： {{item.time}}</span>
                  <span>地点： {{item.add}}</span>
                </p>
              </div>
            </div>
          </div>
          <div class="hot-detail"
               :class="{'hot-detail-active': item.isOpen}">
            <div class="hot-detail-wrap">
              <img class="detail-post" :src="item.post"></img>
              <img class="detail-qr"
                   :src="item.qr">
              <div class="detail-entry">扫码报名</div>
            </div>
            <div class="detail-desc">
              <p>已报名人数： {{item.signNum}}</p>
              <p>报名截止日期： {{item.endTime}}</p>
              <p>活动简介： {{item.intr}}</p>
            </div>
          </div>
        </div>
      </div>
      <!-- <div class="home-friends">
        <h2 class="friends-title">斑马和它的伙伴们</h2>
      </div> -->
    </div>
  </div>
</template>

<script>
import imgSlider from './ImgSlider'

export default {
  data () {
    return {
      hotActv: [{
        isOpen: false,
        post: 'http://facejoin.oss-cn-shenzhen.aliyuncs.com/facejoin/xwtEpGKw7MNbAcST.jpg',
        readNum: 14235,
        title: 'LZ归属 社彩中南” 第十三届社团联合巡礼闭幕式晚会暨 “艺筑中南梦” 第十五届校园文化',
        hoster: '校学生社团联合会',
        time: '2016.05.28 19：30',
        add: '南湖食堂',
        qr: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/4MYK5cy2hFswMfTi.png',
        endTime: '2016.05.25',
        signNum: '253',
        intr: '感受文化中南，大师级讲座，我们相约在这个夏天。感受文化中南，大师级讲座，我们相约在这个夏天。'
      }, {
        isOpen: false,
        post: 'http://facejoin.oss-cn-shenzhen.aliyuncs.com/facejoin/A7XZCcyJy5BsDYsJ.png',
        readNum: 3522,
        title: '武汉大学计算机学院“铭计e生”2016年毕业晚会',
        hoster: '武大计院2012级毕委会',
        time: '2016.06.19 18：00',
        add: '武汉大学计算机学院院办8楼',
        qr: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/KbG3ZSFiAH5rktbk.png',
        endTime: '2016.06.19',
        signNum: '110',
        intr: '光阴似箭，日月如梭。转眼间又到了如火的六月。这个充满快乐也充满感伤的季节。它的快乐是因为充满生机，之所以感伤又是因为有许多人要离开这个生活了四年的校园。“天下没有不散的宴席”，有相聚就会有分离，有快乐就会有悲伤......'
      }, {
        isOpen: false,
        post: 'http://facejoin.oss-cn-shenzhen.aliyuncs.com/facejoin/4kTXjrNCMwHjie23.jpg',
        readNum: 1512,
        title: '这可能是光谷最好玩的线下看球趴了！！',
        hoster: '小斑马个个',
        time: '2016.06.30 00：00',
        add: '武汉市光谷西班牙风情街',
        qr: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/6HCBa54is6kARwfY.png',
        endTime: '2016.06.30 23:30',
        signNum: '5',
        intr: '这可能是光谷周边最好玩的看球party还记得08年的瑞士，12年的波兰吗？又到了4年一度的欧洲杯之夏，4年之前陪你看球的人在哪里，4年之后有没有新的朋友陪你熬夜看球？'
      }, {
        isOpen: false,
        post: 'http://facejoin.oss-cn-shenzhen.aliyuncs.com/facejoin/zfWTCzPyCcf5aybp.png',
        readNum: 1421,
        title: '武汉大学计算机学院2016届毕业生奔跑吧2016定向越野大赛',
        hoster: '武大计院2012级毕委会',
        time: '2016.06.17 17：00',
        add: '武汉大学计算机学院',
        qr: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/fNWc2YGTPTt6yERa.png',
        endTime: '2016.06.01',
        signNum: '24',
        intr: '武汉大学计算机学院2016届毕业生奔跑吧2016定向越野比赛本届定向越野以“团结、交流、互助、共赢”为宗旨，以活跃校园文化，展现我院毕业生风采，提高增强毕业生' +
				'的身体素质为目标，以树立我院本科毕业生积极上进的良好形象，激发同学们的团队精神和竞争意识，在本科生即将毕业离校之际，特开展本次活动。'
      }]
    }
  },
  props: {
    isPublic: false,
    isData: false,
    isCnt: false
  },
  components: {
    imgSlider
  },
  methods: {
    openActv (index) {
      // if (this.hotOpen === index) {
      //   this.hotOpen = -1
      // } else {
      //   this.hotOpen = index
      console.log(this.hotActv[index].isOpen)
      this.hotActv[index].isOpen = !this.hotActv[index].isOpen
        // window.scrollTo(0, this.getOffset(this.$el.querySelectorAll('.hot-item')[index]).top - 60)
      // }
    }
    // getOffset (el) {
    //   let _x = 0
    //   let _y = 0
    //   while (el && !isNaN(el.offsetLeft) && !isNaN(el.offsetTop)) {
    //     _x += el.offsetLeft - (el.tagName !== 'BODY' ? el.scrollLeft : 0)
    //     _y += el.offsetTop - (el.tagName !== 'BODY' ? el.scrollTop : 0)
    //     el = el.offsetParent
    //   }
    //   return {
    //     top: _y,
    //     left: _x
    //   }
    // }
  }
}
</script>

<style lang="less">
@import '../assets/css/index.less';
@import '../assets/css/home-animation.less';

.home {
  position: relative;
  z-index: 0;
  overflow: hidden;
  color: #333;
}
.home-banner {
  position: fixed;
  width: 100%;
  height: 550px;
  height: 90vh;
  overflow: hidden;
}
.home-banner-img {
  height: 100%;
  background: url('http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/WhtdNKXtr3kci7sW.png') center/cover;
  transition: transform 1s ease-out;
  &:hover {
    transform: scale3d(1.06, 1.06, 1);
  }
}
.home-body {
  position: relative;
  margin: 550px 0 0;
  margin: 90vh 0 0;
  background: #fff;
}
.home-title {
  position: absolute;
  left: 43%;
  top: -430px;
  writing-mode: vertical-lr;
  h2 {
    .re-h;
    color: #fff;
    font-size: 40px;
    letter-spacing: 5px;
    cursor: default;
  }
  h3 {
    .re-h;
    margin-top: 80px;
    color: #fff;
    font-size: 20px;
    letter-spacing: 2px;
    cursor: default;
    &::after {
      content: '';
      position: absolute;
      right: 14px;
      bottom: -26px;
      width: 2px;
      height: 20px;
      background: #4ccbc6;
    }
  }
}
.home-section {
  .ui-wrap-1080;
  min-height: 500px;
  font-size: @fs-16;
  overflow: hidden;
  .section-text {
    width: 330px;
    margin: 160px 0 0;
    padding: 0 0 0 150px;
  }
  .section-text-active {
    .section-desc,
    .section-title {
      transform: none;
      opacity: 1;
    }
  }
  .section-show {
    position: relative;
    width: 500px;
    height: 400px;
    margin: 100px 0 0;
  }
  .section-title {
    .re-h;
    font-size: @fs-34;
    line-height: 90px;
    color: #1a1a1a;
    cursor: default;
    transition: all 1s;
    transform: translate3d(0, 100px, 0);
    opacity: 0;
  }
  .section-desc {
    .re-p;
    position: relative;
    line-height: 44px;
    cursor: default;
    transition: all 1s .2s;
    transform: translate3d(0, 100px, 0);
    opacity: 0;
    &::before {
      content: '';
      position: absolute;
      top: 14px;
      left: -20px;
      width: 3px;
      height: 16px;
      background: #4ccbc6;
      transition: transform .3s ease;
    }
  }
}
.section-data {
  .section-text {
    width: 460px;
    padding: 0 0 0 20px;
  }
  .section-show {
    height: 350px;
  }
}
.home-hot {
  padding: 100px 0 130px;
  .hot-title {
    .ui-title;
  }
  .hot-desc {
    .re-p;
    margin: 0 0 24px;
    font-size: @fs-16;
    line-height: 60px;
    text-align: center;
    color: #666;
    span {
      position: relative;
      &::before {
        content: '';
        position: absolute;
        left: -40px;
        top: 8px;
        width: 20px;
        height: 2px;
        background: #4ccbc6;
      }
      &::after {
        content: '';
        position: absolute;
        right: -40px;
        top: 8px;
        width: 20px;
        height: 2px;
        background: #4ccbc6;
      }
    }
  }
  .hot-actv {
    position: relative;
    z-index: 0;
    padding: 50px 0 0;
    background: center/cover;
    cursor: pointer;
    &:hover {
      .hot-actv-masker {
        background: rgba(248, 248, 248, 0.95);
      }
      .hot-actv-wrap {
        transform: translate3d(-50px, 0, 0);
      }
      .actv-read {
        color: #4ccbc6;
      }
    }
  }
  .hot-actv-active {
    .hot-actv-masker {
      background: rgba(248, 248, 248, 0.95);
    }
    .hot-actv-wrap {
      transform: translate3d(-50px, 0, 0);
    }
    .actv-read {
      color: #4ccbc6;
    }
  }
  .hot-actv-masker {
    position: absolute;
    z-index: -1;
    top: 0;
    width: 100%;
    height: 100%;
    background: #fff;
    transition: background-color .3s ease;
  }
  .hot-detail {
    .ui-wrap-1080;
    position: relative;
    height: 0;
    box-shadow: inset 0 -1px rgba(0, 0, 0, 0.2);
    // background: rgba(248, 248, 248, 0.8);
    font-size: @fs-16;
    text-align: center;
    line-height: 1.7;
    color: #666;
    overflow: hidden;
    transition: all .5s ease;
  }
  .hot-detail-active {
    height: 500px;
    margin-bottom: 40px;
    .detail-post,
    .detail-desc {
      transform :translate3d(0, 0, 0);
      opacity: 1;
    }
    .detail-qr {
      transform: translate(-80%, 0);
      opacity: 1;
    }
    .detail-entry {
      transform: translate(-105%, 0);
      opacity: 1;
    }
  }
  .hot-detail-wrap {
    display: inline-block;
    position: relative;
    height: 460px;
    margin: 20px 0;
  }
  .detail-post {
    height: 100%;
    transform: translate3d(0, 80px, 0);
    opacity: 0;
    transition: all 1s;
  }
  .detail-qr {
    position: absolute;
    left: 0;
    bottom: 60px;
    transform: translate3d(-150%, 0, 0);
    width: 100px;
    border: 5px solid #fff;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
    opacity: 0;
    transition: all .8s .5s;
  }
  .detail-entry {
    position: absolute;
    bottom: 30px;
    transform: translate3d(-150%, 0, 0);
    opacity: 0;
    transition: all .8s .6s;
  }
  .detail-desc {
    display: inline-block;
    position: absolute;
    margin: 30px 0 0 20px;
    text-align: left;
    transform: translate3d(50px, 0, 0);
    opacity: 0;
    transition: all 1s .3s;
    p {
      .re-p;
    }
  }
  .hot-actv-wrap {
    .ui-wrap-1080;
    min-height: 100px;
    transition: all .7s ease;
  }
  .actv-read {
    display: inline-block;
    width: 200px;
    text-align: right;
    vertical-align: top;
    color: #bdbdbd;
    transition: all .5s ease;
  }
  .actv-num {
    .re-p;
    font-size: @fs-32;
    line-height: 1;
  }
  .actv-name {
    .re-p;
    font-size: @fs-16;
    line-height: 24px;
  }
  .actv-content {
    display: inline-block;
    margin: 0 0 0 54px;
  }
  .actv-title {
    .re-h;
    font-size: @fs-18;
    line-height: 1;
  }
  .actv-info {
    font-size: @fs-16;
    line-height: 30px;
    color: #666;
    span {
      margin: 0 46px 0 0;
      font-size: @fs-16;
    }
  }
}
.home-friends {
  min-height: 500px;
  padding: 50px 0;
  background: #f8f8f8;
  .friends-title {
    .ui-title;
  }
}
</style>

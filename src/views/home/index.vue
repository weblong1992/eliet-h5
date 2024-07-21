<template>
  <div class="home">
    <div class="logo_box">
      <img src="~@/assets/image/main/logo.png" width="130" />
    </div>

    <div class="xxfw">
      <div class="desc">
        <p>风靡欧美精英圈层的</p>
        <p>定制化学习服务</p>
        <p>专业品质 私奢服务</p>
      </div>

      <div class="bottom_bg">
        <p>首创定制化英语学习模式</p>

        <p>只为1%社会精英阶层服务</p>

        <p>通过语言学习为未来领袖赋能</p>
      </div>
    </div>

    <!-- 用户协议和隐私协议 -->
    <div class="xyBox">
      <!-- `checked` 为 true 或 false -->
      <div>
        <el-input v-model="phone" placeholder="请输入您的手机号" />
      </div>
      <div class="yxTxt">
        <el-checkbox v-model="checked"></el-checkbox>
        <span class="ml-5">我已阅读并同意</span>
        <span class="mycolor">ELIET ENGLISH用户协议</span>
        <b>和</b>
        <span class="mycolor">隐私政策</span>
      </div>
    </div>

    <div class="aboutWe">
      <div class="title">
        <div>关于我们</div>

        <div class="line_bar"></div>
      </div>

      <div class="con">
        Eliet
        Enqlish是一家为全球家庭提供个性化定制英语学习的数智教育平台。公司围绕教育
        服务
        科技三大内核，打破传统课程平台内容的束缚，以个性化学习定制为切入点，构建出一套适合不同孩子的专属语言学习生态圈。以专业的教学品质，满足不同年龄，不同地域，不同文化背景孩子的个性化语言学习要求。
      </div>

      <div class="wIcon">
        <img src="~@/assets/image/main/w1.png" width="101" />
        <img src="~@/assets/image/main/w2.png" width="101" />
        <img src="~@/assets/image/main/w3.png" width="101" />
      </div>
    </div>
    <!-- <div class="reason">
      <div class="tit">选择 <span class="ee">Eliet English</span>的理由</div>

      <div class="content">
        <div class="item">
          <div class="img_box">
            <img src="~@/assets/image/main/a1.png" width="168" />
          </div>
          <div class="bar">
            <div>定制化的学习内容</div>
          </div>
        </div>

        <div class="item">
          <div class="img_box">
            <img src="~@/assets/image/main/a2.png" width="168" />
          </div>
          <div class="bar">
            <div>四对一服务专属服务</div>
          </div>
        </div>

        <div class="item">
          <div class="img_box">
            <img src="~@/assets/image/main/a3.png" width="168" />
          </div>
          <div class="bar">
            <div>多元化学习体系</div>
          </div>
        </div>

        <div class="item">
          <div class="img_box">
            <img src="~@/assets/image/main/a4.png" width="168" />
          </div>
          <div class="bar">
            <div>智能化的学习方式</div>
          </div>
        </div>

        <div class="item">
          <div class="img_box">
            <img src="~@/assets/image/main/a5.png" width="168" height="100" />
          </div>
          <div class="bar">
            <div>专业英美外教</div>
          </div>
        </div>

        <div class="item">
          <div class="img_box">
            <img src="~@/assets/image/main/a6.png" width="168" height="100" />
          </div>
          <div class="bar">
            <div>国际化的培养策略</div>
          </div>
        </div>
      </div>
    </div> -->

    <div class="selct_reason">
      <img src="~@/assets/image/main/season.png" width="365" />
    </div>

    <div class="cpfw">
      <img src="~@/assets/image/main/cpfw.png" width="350" />
    </div>

    <div class="yxjs">
      <img src="~@/assets/image/main/yxjs.png" :width="setWidth" />
    </div>

    <div class="dzhxx">
      <div class="title">
        <div>
          <p>真正的定制化学习</p>
          <p>是课程匹配孩子</p>
        </div>

        <div class="line_bar"></div>
      </div>

      <div class="con">
        打破市面机构传统课程学习方式，根据学员语言基础、兴趣爱好、目标方向定制专属课程发挥每个学员个体的优势
        量身打造最适合的学习计划。
      </div>
    </div>

    <div class="gjtd">
      <img src="~@/assets/image/main/gjtd.png" :width="setWidth" />
    </div>

    <div class="smfw">
      <img src="~@/assets/image/main/smfw.png" width="345" />
    </div>

    <div class="xxqc">
      <img src="~@/assets/image/main/xxqc.png" />
    </div>

    <div class="dzh">
      <img src="~@/assets/image/main/dzh.png" />
    </div>

    <div class="ljkq">
      <img src="~@/assets/image/main/ljqk.png" width="344" />

      <div class="txt" @click="ljlq">立即开启 ></div>
    </div>

    <div class="qssk">
      <img src="~@/assets/image/main/qssk.png" />

      <div class="operate">
        <!-- <el-input
          v-model="phone"
          @input="handInput"
          placeholder="请输入手机号"
        />
       -->

        <div class="ljlq">
          <div class="ljlq_inner" @click="ljlq">立即开启</div>
        </div>
      </div>
    </div>

    <!-- 客服热线 -->
    <div class="kfrx">
      <div class="kfrx_left">
        <!-- <div class="kfrx_txt">客服热线</div>
        <div class="line_bar">
          <img src="~@/assets/image/main/line_bar.png" width="32" />
        </div>

        <div class="phone">
          <img src="~@/assets/image/main/dh.png" width="25" />

          <div class="phone_txt">010-00000000</div>
        </div> -->

        <div class="worktime">周一至周日08：00-22：00</div>

        <div class="zxzx">在线咨询</div>
      </div>

      <div class="kfrx_right">
        <div class="tit">官方公众号</div>
        <div class="pic">
          <img src="~@/assets/image/main/gzh.jpg" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      checked: false,
      dialogVisible: false,
      setWidth: document.documentElement.clientWidth,
      phone: "",
    };
  },
  methods: {
    // open() {
    //   if (this.phone && this.phone.length === 11) {
    //     this.$store.commit("setRegisterDia", true);
    //     this.$store.commit("setPhone", this.phone);
    //   } else {
    //     if (!this.phone) {
    //       this.$message({
    //         message: "请输入手机号",
    //         type: "warning",
    //       });
    //     } else if (this.phone.length < 11 && this.phone.length > 0) {
    //       this.$message({
    //         message: "手机号位数不正确",
    //         type: "warning",
    //       });
    //     }
    //   }
    // },
    // handInput(value) {
    //   this.phone = value.replace(/[^\d]/g, "");
    // },
    ljlq() {
      this.$store.commit("setRegisterDia", true);
      // this.open();
    },
    // ljkq() {
    //   // this.$store.state.phone = "";
    //   this.$store.commit("setRegisterDia", true);
    // },
  },
  created() {},
};
</script>
<style lang="scss" scoped>
.home {
  width: 100%;
  height: 100%;

  .logo_box {
    display: flex;
    justify-content: center;
    padding: 20px 0;
  }

  .xxfw {
    height: 600px;
    background-image: url("~@/assets/image/main/bgyy.png"),
      url("~@/assets/image/main/bg.png");
    background-repeat: no-repeat;
    background-size: cover;
    position: relative;

    & .desc {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-top: 80px;
      color: #fff;
      font-size: 28px;
    }

    & .bottom_bg {
      width: 360px;
      height: 141px;
      background-image: url("~@/assets/image/main/bottom_bg.png");
      background-repeat: no-repeat;
      background-size: cover;
      position: absolute;
      bottom: -70px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      font-size: 22px;
      color: #fff;
      & > p {
        margin-bottom: 5px;
      }
    }
  }

  .xyBox {
    margin-top: 120px;
    padding: 0 20px;

    .yxTxt {
      display: flex;
      align-items: center;
      font-size: 12px;
      margin-top: 10px;

      .ml-5 {
        margin-left: 5px;
      }

      .mycolor {
        color: $mainColor;
      }
    }
  }
  .aboutWe {
    padding: 0 20px;
    // padding-top: 120px;
    padding-top: 60px;

    & .title {
      display: flex;
      flex-direction: column;
      align-items: center;
      font-size: 26px;

      & .line_bar {
        width: 40px;
        height: 2px;
        background-color: $mainColor;
        margin-top: 20px;
        margin-bottom: 30px;
      }
    }

    & .con {
      font-size: 12px;
    }

    & .wIcon {
      display: flex;
      justify-content: center;
      padding-top: 40px;
      padding-bottom: 60px;

      & > img {
        margin-right: 10px;
      }
    }
  }

  .reason {
    height: 600px;
    background-color: $areaBgColor;
    & .tit {
      display: flex;
      justify-content: center;
      padding: 20px 0;

      .ee {
        color: $mainColor;
      }
    }

    & .content {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      padding: 0 10px;

      & > .item {
        width: 168px;
        display: flex;
        flex-direction: column;

        & .bar {
          width: 168px;
          height: 30px;
          background-image: url("~@/assets/image/main/bar.png");
          background-repeat: no-repeat;
          display: flex;
          justify-content: center;
          align-items: center;
          color: #fff;
        }
      }

      & > .item:nth-child(2n + 1) {
        margin-right: 15px;
      }
    }
  }

  .selct_reason {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 600px;
    background-color: $areaBgColor;
  }

  .cpfw {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 300px;
    margin: 100px 0;
  }

  .dzhxx {
    padding: 40px 20px;
    & .title {
      display: flex;
      flex-direction: column;
      align-items: center;
      font-size: 26px;

      & .line_bar {
        width: 40px;
        height: 2px;
        background-color: $mainColor;
        margin-top: 20px;
        margin-bottom: 30px;
      }
    }
  }

  .smfw {
    display: flex;
    align-items: center;
    justify-content: center;
    padding-top: 30px;
  }

  .xxqc {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 40px 0;
    & > img {
      width: 100%;
    }
  }

  .dzh {
    // width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 40px 0;
    & > img {
      width: 100%;
    }
  }

  .ljkq {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;

    .txt {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      color: #fff;
    }
  }

  .qssk {
    display: flex;
    // justify-content: center;
    align-items: center;
    margin: 40px 0;
    position: relative;
    & > img {
      width: 100%;
    }

    & .operate {
      position: absolute;
      left: 20px;
      margin-top: -40px;

      & /deep/ .el-input__inner {
        width: 90px;
        color: #000000;
        height: 20px;
      }

      & /deep/ input::-webkit-input-placeholder {
        color: #ccc;
        font-size: 8px;
        position: absolute;
        left: 2px;
      }

      .ljlq {
        margin-top: 3px;
        .ljlq_inner {
          width: 83px;
          height: 20px;
          border-radius: 20px;
          background-color: $mainColor;
          display: flex;
          justify-content: center;
          align-items: center;
          color: #fff;
          font-size: 12px;
        }
      }
    }
  }

  .kfrx {
    display: flex;
    justify-content: space-between;
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 20px;
    padding-bottom: 60px;
    background-color: #000000;

    .kfrx_left {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      .kfrx_txt {
        color: #fff;
      }
      .phone {
        padding: 20px 0;
        display: flex;

        .phone_txt {
          margin-left: 10px;
          color: #fff;
        }
      }

      .worktime {
        font-size: 12px;
        color: #ccc;
      }

      .zxzx {
        width: 95px;
        height: 27px;
        margin-top: 20px;
        background-image: url("~@/assets/image/main/btn.png");
        background-repeat: no-repeat;
        background-size: 100% 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        color: #fff;
      }
    }

    .kfrx_right {
      color: #fff;

      .pic {
        & > img {
          width: 150px;
          height: 150px;
        }
      }
    }
  }
}
</style>

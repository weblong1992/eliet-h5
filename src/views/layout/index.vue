<template>
  <div class="layout">
    <!-- <Vheader /> -->
    <div class="main">
      <router-view class="page" />

      <div class="dialog_box">
        <el-dialog
          center
          title="开启定制"
          :visible.sync="dialogVisible"
          width="95%"
          @close="close"
        >
          <el-dialog
            width="95%"
            :title="num === 1 ? '用户协议' : '隐私政策'"
            :visible.sync="innerVisible"
            append-to-body
          >
            <div>
              <UserAgreement v-if="num === 1" />

              <PrivacyPolicy v-if="num === 2" />
            </div>
          </el-dialog>

          <!-- 弹窗 -->
          <el-form ref="ruleForm" label-width="0px" class="demo-ruleForm">
            <div class="inputDeep">
              <el-form-item label="">
                <el-input
                  v-model="form.name"
                  class="myInput"
                  placeholder="孩子姓名/Name"
                >
                  <template #prefix>
                    <div class="prefix">
                      <img
                        src="~@/assets/image/common/xm.png"
                        alt=""
                        width="16"
                      />
                    </div>
                  </template>
                </el-input>
              </el-form-item>
            </div>

            <div>
              <el-form-item label="">
                <el-input
                  class="myInput"
                  maxlength="11"
                  v-model="form.phone"
                  placeholder="手机号/Phone"
                  @input="handInput1"
                >
                  <template #prefix>
                    <div class="prefix">
                      <img
                        src="~@/assets/image/common/dh.png"
                        alt=""
                        width="16"
                      />
                    </div>
                  </template>
                </el-input>
              </el-form-item>
            </div>

            <div>
              <el-form-item label="">
                <el-input
                  v-model="form.code"
                  maxlength="6"
                  @input="handInput2"
                  class="myInput yzm"
                  placeholder="请输入验证码"
                >
                  <template #prefix>
                    <div class="prefix">
                      <img
                        src="~@/assets/image/common/yx.png"
                        alt=""
                        width="16"
                      />
                    </div>
                  </template>

                  <template #suffix>
                    <div class="suffix">
                      <el-button
                        v-show="sendAuthCode"
                        size="mini"
                        class="mybtn"
                        @click.prevent="getAuthCode"
                        >获取验证码</el-button
                      >

                      <span v-show="!sendAuthCode" class="auth_text">
                        <span class="auth_text_blue">{{ auth_time }} </span>
                        秒之后重新发送</span
                      >
                    </div>
                  </template>
                </el-input>
              </el-form-item>
            </div>
            <!-- 用户协议和隐私协议 -->
            <div class="xyBox">
              <!-- `checked` 为 true 或 false -->

              <div class="yxTxt">
                <el-checkbox v-model="checked"></el-checkbox>
                <span class="ml-5">我已阅读并同意</span>
                <span class="mycolor" @click="agreement(1)"
                  >ELIET ENGLISH用户协议</span
                >
                <b>和</b>
                <span class="mycolor" @click="agreement(2)">隐私政策</span>
              </div>
            </div>
          </el-form>
          <span slot="footer" class="dialog-footer">
            <el-button class="submitBtn" @click="register">提交申请</el-button>
          </span>
        </el-dialog>
      </div>

      <!-- 注册成功弹窗 -->
      <div class="dialog_box">
        <el-dialog
          top="20vh"
          title="注册成功"
          :visible="successDiaFlag"
          width="96%"
          @close="handleColse"
        >
          <div class="img_box">
            <img src="~@/assets/image/common/success.jpg" width="300" />
          </div>
        </el-dialog>
      </div>

      <div class="fix-footer">
        <div class="desc">Eliet English邀您开启定制化学习之旅</div>
        <!-- <el-input
            placeholder="请输入您的手机号"
            v-model="form.phone"
            @input="handInput"
          /> -->
        <div class="btnbox">
          <el-button size="mini" class="toget" @click="ljlq"
            >立即开启</el-button
          >
        </div>
      </div>

      <!-- 悬浮框 -->
      <!-- <div class="fixed-contain">
        <div>
          <div>
            <img src="~@/assets/image/home/zxzx.png" width="36" height="34" />
          </div>

          <div>在线咨询</div>
        </div>

        <div>
          <div>
            <img src="~@/assets/image/home/qywx.png" width="32" height="32" />
          </div>

          <div>企业微信</div>
        </div>

        <div>
          <div>
            <img src="~@/assets/image/home/gzh.png" width="32" height="32" />
          </div>

          <div>公众号</div>
        </div>
      </div> -->
    </div>
    <!-- <VFooter /> -->
  </div>
</template>
<script>
// import Vheader from "@/components/v-header/index.vue";
// import VFooter from "@/components/v-footer/index.vue";
import UserAgreement from "./UserAgreement.vue";
import PrivacyPolicy from "./PrivacyPolicy.vue";
import { GetCode, Register } from "@/api/register.js";

export default {
  components: {
    // Vheader,
    // VFooter,
    UserAgreement,
    PrivacyPolicy,
  },
  data() {
    return {
      num: 1, //1 用户协议 2 演示政策
      checked: true,
      mobile: "",
      // form.phone: "",
      successDiaFlag: false,

      dialogVisible: false,
      innerVisible: false,
      form: {
        name: "",
        phone: "",
        code: "",
      },
      sendAuthCode: true, //显示‘获取按钮'还是'倒计时'
      auth_time: 0 /*倒计时 计数器*/,
    };
  },
  watch: {
    "$store.state.isShowRegisterDia": {
      handler: function (newVal, oldVal) {
        if (newVal) {
          this.dialogVisible = true;
          this.form.phone = this.$store.state.phone;

          if (!this.$store.state.phone) {
            if (this.form.name || this.form.code) {
              this.form.name = "";
              this.form.code = "";
            }
          }
        }
      },
    },
  },
  methods: {
    // handInput(value) {
    //   // console.log(value);
    //   this.form.phone = value.replace(/[^\d]/g, "");
    // },
    // handInput(value) {
    //   const validPattern = /^[0-9]*$/;
    //   if (!validPattern.test(value)) {
    //     this.mobile = value.replace(/[^0-9]/g, "");
    //   }
    // },
    handInput1(value) {
      const validPattern = /^[0-9]*$/;
      if (!validPattern.test(value)) {
        this.form.phone = value.replace(/[^0-9]/g, "");
      }

      if (!this.form.phone) {
        this.$store.commit("setPhone", "");
      }
    },
    handInput2(value) {
      const validPattern = /^[0-9]*$/;
      if (!validPattern.test(value)) {
        this.form.code = value.replace(/[^0-9]/g, "");
      }
    },
    getAuthCode() {
      if (!this.form.phone) {
        this.$message({
          type: "warning",
          message: "请输入手机号",
        });
        return;
      }

      if (this.form.phone.length > 0 && this.form.phone.length < 11) {
        this.$message({
          type: "warning",
          message: "请输入十一位数手机号",
        });
        return;
      }

      this.getCode();
      this.sendAuthCode = false;
      this.auth_time = 60;

      let auth_timetimer = window.setInterval(() => {
        this.auth_time--;
        if (this.auth_time <= 0) {
          this.sendAuthCode = true;
          window.clearInterval(auth_timetimer);
        }
      }, 1000);
    },
    getCode() {
      let data = {
        region: "86",
        phone: this.form.phone,
      };
      GetCode(data)
        .then((res) => {
          // console.log(res.data);
          if (res.status === 200) {
            this.$message({
              type: "success",
              message: res.message,
            });
          } else {
            this.$message({
              type: "warning",
              message: res.message,
            });
          }
        })
        .catch((err) => {
          console.log(err);
        });
    },
    register() {
      if (!this.form.name) {
        this.$message({
          type: "warning",
          message: "请输入姓名",
        });
        return;
      } else if (!this.form.phone) {
        this.$message({
          type: "warning",
          message: "请输入手机号",
        });
        return;
      } else if (!this.form.code) {
        this.$message({
          type: "warning",
          message: "请输入验证码",
        });
        return;
      } else if (!this.checked) {
        this.$message({
          type: "warning",
          message: "需要同意ELIET ENGLISH用户协议哦~",
        });
        return;
      }

      let data = {
        code: this.form.code,
        nickname: this.form.name,
        phone: this.form.phone,
      };
      Register(data)
        .then((res) => {
          // console.log(res);
          if (res.status == 200) {
            // this.$message({
            //   type: "success",
            //   message: res.message,
            // });

            this.close();

            this.successDiaFlag = true;
          } else {
            this.$message({
              type: "warning",
              message: res.message,
            });
          }
        })
        .catch((err) => {
          console.log(err);
        });
    },
    close() {
      this.$store.commit("setRegisterDia", false);
      this.dialogVisible = false;
    },
    ljlq() {
      this.$store.commit("setRegisterDia", true);
      this.$store.commit("setPhone", "");
    },
    // open() {
    //   if (this.form.phone && this.form.phone.length === 11) {
    //     this.$store.commit("setRegisterDia", true);
    //     this.$store.commit("setPhone", this.form.phone);
    //   } else {
    //     if (!this.form.phone) {
    //       this.$message({
    //         message: "请输入手机号",
    //         type: "warning",
    //       });
    //     } else if (this.form.phone.length < 11 && this.form.phone.length > 0) {
    //       this.$message({
    //         message: "手机号位数不正确",
    //         type: "warning",
    //       });
    //     }
    //   }
    // },
    agreement(num) {
      console.log(num);
      this.num = num;
      this.innerVisible = true;
    },
    handleColse() {
      this.successDiaFlag = false;
    },
  },
};
</script>
<style lang="scss" scoped>
.layout {
  width: 100%;
  height: 100%;

  // .main {
  //   margin-top: 90px;
  // }

  .main {
    width: 100%;
    height: 100%;
  }
}

.fixed-contain {
  position: fixed;
  right: 0;
  top: 50%;
  margin-top: -140px;
  z-index: 100;
  width: 82px;
  height: 279px;
  background-image: url("~@/assets/image/home/xfj.png");
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  & > div {
    margin-bottom: 20px;
    font-size: 12px;
    cursor: pointer;

    & > div:nth-child(1) {
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
}

.fix-footer {
  position: fixed;
  left: 0;
  bottom: 0;
  z-index: 20;
  width: 100%;
  height: 56px;
  background: $mainColor;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 20px;

  // & .el-form {
  //   height: 100%;
  //   display: flex;
  //   align-items: center;
  // }

  & .desc {
    flex: 1;
    display: flex;
    flex-wrap: wrap;
    font-size: 20px;
    color: #ffffff;
    // margin-right: 15px;
  }

  // & .el-input {
  //   width: 260px;
  //   height: 42px;
  //   display: flex;
  //   align-items: center;
  //   // line-height: 42px;
  //   border-radius: 25px;
  //   border: none;
  //   outline: none;
  //   padding: 0 10px;
  //   margin: 0 20px;
  // }

  // & /deep/ .el-input__inner {
  //   &::placeholder {
  //     // color: red;
  //     font-size: 18px;
  //   }
  // }

  & .btnbox {
    flex: 1;
    padding-left: 20px;

    & .toget {
      background-color: #ffffff;
      border: none;
      outline: none;
      color: $mainColor;
      font-size: 18px;
    }
  }
}

.myInput /deep/ .el-input__inner {
  border-radius: 0; // 去除圆角
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
  border-bottom-width: 1px;
  border-color: $mainColor; //边框的颜色
}

.myInput /deep/ .el-input__inner::-webkit-input-placeholder {
  padding-left: 10px;
}

.yzm .mybtn {
  background-color: $mainColor;
  color: #fff;
}

.submitBtn {
  background-color: $mainColor;
  color: #fff;
}

.auth_text_blue {
  color: #409eff;
}
.xyBox {
  // margin-top: 120px;
  // padding: 0 20px;
  .yxTxt {
    display: flex;
    align-items: center;
    font-size: 10px;
    margin-top: 10px;

    // .ml-5 {
    //   margin-left: 5px;
    // }

    .mycolor {
      color: $mainColor;
      cursor: pointer;
    }
  }
}

.dialog_box ::v-deep .el-dialog {
  opacity: 0.9;

  & .img_box {
    display: flex;
    justify-content: center;
    padding: 20px;
  }
}
</style>

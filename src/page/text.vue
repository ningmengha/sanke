<template>
    <div class="login_page fillcontain">
        <div class="pic"><img src="images/figure_1.png" alt=""></div>
        <transition name="form-fade" mode="in-out">
            <section class="form_contianer" v-show="showLogin">
                <!-- <div class="manage_tip">
                    <p>淘亿批发管理系统</p>
                </div> -->
                <el-form :model="loginForm" :rules="rules" ref="loginForm" label-width="90px" class="demo-loginForm qf">
                    <!-- v-model="loginForm.username"  v-model=""  -->
                    <div class="login-left fl">
                        <el-form-item label="账号：" prop="username">
                            <el-input v-model="loginForm.username"></el-input>
                        </el-form-item>
                        <el-form-item label="密码：" prop="password">
                            <el-input type="password" v-model="loginForm.password" auto-complete="off"></el-input>
                        </el-form-item>
                        <el-form-item label="验证码：" prop="checkNode">
                            <el-input v-model="loginForm.code" id="inputCode"></el-input>
                            <i id="right"></i>
                            <span class="codeimg" id="codeimg"></span>
                        </el-form-item>
                    </div>
                    <div class="line fl"></div>
                    <div class="login-right fl">
                        <el-form-item>
                            <el-button type="primary" @click="submitForm('loginForm') class=" submit_btn "">登录</el-button>
                        </el-form-item>
                    </div>
                </el-form>
            </section>
        </transition>
    </div>
</template>
<script>
import { login, getAdminInfo } from '@/api/getData'
import { mapActions, mapState } from 'vuex'

export default {
    data() {
        return {
            loginForm: {
                username: '',
                password: '',
            },
            rules: {
                username: [
                    { required: true, message: '请输入用户名', trigger: 'blur' },
                ],
                password: [
                    { required: true, message: '请输入密码', trigger: 'blur' }
                ],
            },
            showLogin: false,
        }
    },
    mounted() {
        this.showLogin = true;
        if (!this.adminInfo.id) {
            this.getAdminData()
        }
    },
    computed: {
        ...mapState(['adminInfo']),
    },
    methods: {
        ...mapActions(['getAdminData']),
        async submitForm(formName) {
            this.$refs[formName].validate(async(valid) => {
                if (valid) {
                    const res = await login({ user_name: this.loginForm.username, password: this.loginForm.password })
                    if (res.status == 1) {
                        this.$message({
                            type: 'success',
                            message: '登录成功'
                        });
                        this.$router.push('manage')
                    } else {
                        this.$message({
                            type: 'error',
                            message: res.message
                        });
                    }
                } else {
                    this.$notify.error({
                        title: '错误',
                        message: '请输入正确的用户名密码',
                        offset: 100
                    });
                    return false;
                }
            });
        },
    },
    watch: {
        adminInfo: function(newValue) {
            if (newValue.id) {
                this.$message({
                    type: 'success',
                    message: '检测到您之前登录过，将自动登录'
                });
                this.$router.push('manage')
            }
        }
    }
}

</script>
<style lang="less" scoped>
@import '../style/mixin';

.qf {
    *zoom: 1;
}

.qf:after {
    content: '';
    display: table;
    clear: both;
}

.fl {
    float: left;
}

.fr {
    float: right;
}

.login_page {
    width: 100%;
    height: 100%;
    padding-top: 60px;
    padding-left: 105px;
    background: #7bc4f9 url("../images/background_1.jpg") no-repeat top center;
    box-sizing: border-box;
}

.login_page .pic {
    width: 263px;
    height: 121px;
    margin-left: 130px;
    margin-bottom: 30px;
}

.login_page .pic img {
    width: 100%;
    vertical-align: top;
}

.login_page .demo-loginForm {
  width: 480px;
  padding: 24px 0 22px;
  background: #afdbfb;
  box-sizing: border-box;
  border-radius: 10px;
}

.login_page .demo-loginForm .el-input {
  width: 160px;
}

.login_page .demo-loginForm .login-left {
  width: 310px;
}

.login_page .demo-loginForm .login-left .el-form-item {
  margin-bottom: 18px;
}

.login_page .demo-loginForm .login-left .el-form-item .el-form-item__label {
  padding: 7px 12px 7px 0;
  color: #333;
}

.login_page .demo-loginForm .login-left .el-form-item .el-form-item__content {
  line-height: 28px;
}

.login_page .demo-loginForm .login-left .el-form-item .el-input__inner {
  height: 28px;
  border: 1px solid #ccc;
}

.login_page .demo-loginForm .login-left .el-form-item:last-child {
  margin-bottom: 0;
}
.login_page .demo-loginForm .login-left .el-form-item:last-child .el-input {
  width: 98px;
}
.login_page .demo-loginForm .login-left .el-form-item:last-child .codeimg {
  display: inline-block;
  width: 76px;
  height: 28px;
  margin-left: 12px;
  vertical-align: bottom;
}
.login_page .demo-loginForm .login-left .el-form-item:last-child .codeimg img {
  width: 100%;
  vertical-align: top;
}
.login_page .demo-loginForm .line {
  margin-top: 10px;
  width: 1px;
  height: 100px;
  background: #fff;
}
.login_page .demo-loginForm .login-right .el-form-item .el-form-item__content {
  margin-left: 28px!important;
}
.login_page .demo-loginForm .login-right .el-form-item .el-button {
  padding: 7px 42px 8px;
  color: #333;
  margin-top: 44px;
}
.login_page .demo-loginForm .login-right .el-form-item .el-button:focus,
.login_page .demo-loginForm .login-right .el-form-item .el-button:hover {
  border-color: #7bc4f9;
}
.login_page .txt {
  padding-left: 24px;
  margin-top: 16px;
  font-size: 14px;
  line-height: 14px;
  color: #fff;
}


.manage_tip {
    position: absolute;
    width: 100%;
    top: -100px;
    left: 0;
    p {
        font-size: 34px;
        color: #fff;
    }
}

.tip {
    font-size: 12px;
    color: red;
}

.form-fade-enter-active,
.form-fade-leave-active {
    transition: all 1s;
}

.form-fade-enter,
.form-fade-leave-active {
    transform: translate3d(0, -50px, 0);
    opacity: 0;
}

</style>

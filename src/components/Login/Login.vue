<template>
    <div class="login-wrap">
        <div class="sb-login">
            <div class="sb-title">分享日记</div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="0px" class="sb-content">
                <!-- 用户名输入框 -->
                <el-form-item props="userAccount">
                    <el-input v-model="ruleForm.userAccount" placeholder="请输入用户名">
                        <el-button slot="prepend" icon="sb-people"></el-button>
                    </el-input>
                </el-form-item>
                <!-- 用户密码输入框 -->
                <el-form-item prop="userPassword">
                    <el-input type="password" placeholder="请输入密码" v-model="ruleForm.userPassword" @keyup.enter.native="submitForm('ruleForm')">
                        <el-button slot="prepend" icon="sb-lock"></el-button>
                    </el-input>
                </el-form-item>
                <!-- 记住我 和 忘记密码 -->
                <div class="login-set">
                    <el-checkbox size="mini">记住我</el-checkbox>
                </div>
                <div class="login-forgetpwd">
                    <el-button class="forgetPwd" type="text">忘记密码</el-button>
                </div>
                <!-- 登录按钮 和 注册按钮 -->
                <div class="login-btn">
                    <el-button type="primary" @click="submitForm('ruleForm')">登录</el-button>
                </div>
                <div class="register-btn">
                    <el-button type="primary" @click="submitForm('ruleForm')">注册</el-button>
                </div>
            </el-form>
        </div>
    </div>
</template>

<script>
export default {
    name: "login",
    data: function() {
        return {
            ruleForm: {
                userAccount: "",
                userPassword: ""
            },
            rules: {
                userAccount: [
                    // {required: true, message: '请输入用户名', trigger: 'blur' }
                ],
                userPassword: [
                    // {required: true, message: '请输入密码', trigger: 'blur' }
                ]
            }
        };
    },
    methods: {
        submitForm(fromName) {
            this.$refs[fromName].validate(volid => {
                if (valid) {
                    localStorage.setItem("sb_userAccount", this.ruleForm.userAccount);
                    this.$rules.push("/");
                } else {
                    console.log("error submit!");
                    return false;
                }
            });
        }
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.login-wrap {
    position: relative;
    width: 100%;
    height: 100%;
    background-image: url(../../../src/assets/icon/login_background.png);
    background-size: 100%;
}

.sb-title {
    width: 100%;
    line-height: 50px;
    text-align: center;
    font-size: 20px;
    color: firebrick;
    border-bottom: 1px solid #ddd;
}

.sb-login {
    position: absolute;
    left: 50%;
    top: 50%;
    width: 350px;
    margin: -190px 0 0 -175px;
    border-radius: 5px;
    background: rgba(255, 255, 255, 1);
    overflow: hidden;
}

.sb-content {
    padding: 30px 30px;
}

.login-set {
    text-align: left;
}

.login-set .el-checkbox {
    width: 50%;
    color: rgb(167, 160, 160);
    height: 32px;
}

.login-forgetpwd {
    text-align: right;
}

.login-forgetpwd button {
    width: 50%;
    height: 32px;
}

.login-btn {
    text-align: left;
    display: inline;
}

.login-btn button {
    width: 77%;
    height: 36px;
    margin-bottom: 10px;
}

.register-btn {
    text-align: right;
    display: inline;
}

.register-btn button {
    width: 20%;
    height: 36px;
    margin-bottom: 10px;
    background-color: #ddd;
    border: white;
}
</style>

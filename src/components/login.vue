<template>
    <div class="login">
        <div class="loginbox">
            <div class="imgwrap">
                <img src="../assets/logo.png" alt="">
            </div>
            <el-form label-width="0px" class="form"  :model="formdata" :rules="rules" ref="loginForm">
                <el-form-item prop="name">
                    <el-input v-model="formdata.name"></el-input>
                </el-form-item>
                <el-form-item prop="pwd">
                    <el-input v-model="formdata.pwd" type="password"></el-input>
                </el-form-item>
                <el-form-item class="btn">
                    <el-button type="primary" @click="login">登錄</el-button>
                    <el-button type="info" @click="reset">重置</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            formdata: {
                name: '',
                pwd: ''
            },
            rules: {
                name: [
                    { required: true, message: '请输入用戶名', trigger: 'blur' },
                    { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'blur' }
                ],
                pwd: [
                    { required: true, message: '请输入密碼', trigger: 'blur' },
                    { min: 6, max: 15, message: '长度在 6 到 15 个字符', trigger: 'blur' }
                ]
            }
        }
    },
    methods: {
        reset: function() {
            console.log(this);
            this.$refs.loginForm.resetFields();
        },
        login: function() {
            if (this.formdata.name === 'zcy' && this.formdata.pwd === '123456') {
                return this.$router.push('/home')
            }
            this.$message.error('用戶名或密碼錯誤');
        }
    }
};
</script>

<style lang="less" scoped>
    .login {
        height: 100%;
        background-color: #2d4d6d;
        .loginbox {
            width: 500px;
            height: 350px;
            background-color: #fff;
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            .imgwrap {
                width: 200px;
                height: 200px;
                padding: 10px;
                border-radius: 50%;
                border: 1px solid #ccc;
                box-shadow: 0 0 10px #000;
                position: absolute;
                left: 50%;
                transform: translate(-50%,-50%);
                background-color: #fff;
                img {
                    border-radius: 50%;
                    background-color: #eee;
                }
            }
            .form {
                position: absolute;
                bottom: 0;
                width: 100%;
                padding: 0 20px;
                box-sizing: border-box;
                .btn {
                    float: right;
                }
            }
        }
    }
</style>
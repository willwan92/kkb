<template>
    <div>
        <h3>Element表单</h3>
        <hr>
        
        <el-form :model="formData" ref="elForm" :rules="formRules" label-width="80px">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="formData.username"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="formData.password"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="onSubmit('elForm')">登录</el-button>
            </el-form-item>
        </el-form>
        
    </div>
</template>
<script>
export default {
    data() {
        return {
            formData: {
                username: '',
                password: ''
            },
            formRules: {
                username: [
                    { required: true, message: '请输入用户名', trigger: 'blur'}
                ],
                password: [
                    { required: true, message: '请输入密码', trigger: 'blur'}
                ]
            }
        }
    },
    methods: {
        onSubmit(form) {
            this.$refs[form].validate(valid => {
                if (valid) {
                    alert('提交登录')
                } else {
                    alert('校验失败')
                }
            })
        }
    }
}
</script>